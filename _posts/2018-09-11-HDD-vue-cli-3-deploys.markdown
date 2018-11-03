---
layout: post
title:  "Deploying a Vue-cli 3 app with all the bells and whistles"
date:   2018-09-11 21:19
categories: vue webdev
image: /public/images/Vue.js_Logo.svg.png
excerpt: <p>...as painfully as possible.</p>
---

...as painfully as possible.

I started a fresh project that I wanted to use as an excuse to dabble in some new tooling and technologies that I had on my "to-try" list. A. mixture of chats with colleagues and articles from weekly newsletters for devops and javascript had got me pretty hyped to upgrade how I deploy webapp projects going forward.

However, after spinning up a new vue app complete with Typescript, vue-class etc. I needed to deploy my app with a minimal server and suddenly the articles and docs were less obvious.

Below are the steps that I wanted to follow:

1. Build production version of the app `npm run build`
2. Serve static assets and main app from production dist folder locally with a minimal server.
3. Dockerize the dev and production builds with a multistage Dockerfile and [recommended best practices](https://nodesource.com/blog/containerizing-node-js-applications-with-docker)
4. Spin up dockerized version of app with Kubernetes
5. Deploy kubernetes version to Google Cloud or similar
6. Automate future deployments
7. Enjoy brief joy before completely new hype train arrives.

This article aims to capture my journey through these recipe steps. I hope that writing about my experience with each step (debugging + blogging = **_deblogging_?** 🤔) _as I'm developing_ helps someone out there apart from myself as they too google their way through some hype-driven-development. At the very least it helps force me to explain my actions to myself as I go...like pair-coding...with myself.


## 1. Build production version of app `ERROR  Failed to compile with 39 errors`
Tslint errors to be specific. I dealt with them as follows:

* **`Parameter '_' implicitly has an 'any' type.`** - [a quick google](https://stackoverflow.com/questions/43064221/typescript-ts7006-parameter-xxx-implicitly-has-an-any-type) suggested that I could either go back through my hacked code and set explicit types OR I could make the tslinting less strict with `"strict": false` in my `tsconfig.json` file. I went with the latter...but it STILL did not prevent my `npm run build` from failing. Now I was down to 17 errors.

* **`Property 'days' does not exist on type 'object'.`** - [another google](https://stackoverflow.com/questions/36607979/how-to-get-around-property-does-not-exist-on-object) was really pushing that I should be more explicit setting types on variables and parameters that I was using. This seemed less likely to be quick-fixable until I realised that I had somehow set a proptype as an `object` and Typescript was expecting a few more details about that object. I set it to `any` instead - down to 13 errors now!

* **`Module '"/node_modules/moment/moment"' has no default export.`** - I managed to squash this complaint by adding `"allowSyntheticDefaultImports": true` to the `tsconfig.json` thanks to this [hint](https://stackoverflow.com/questions/36893165/importing-moment-into-typescript-project#comment61356347_36893860). Down to 11 errors now.


* **`Cannot find name 'array'.`** - For extra clarity here's the line that it was complaining about: `@Prop() public events!: array;`. This looks ok-ish to me as a concept - surely that's legit typescripting and maybe `array` should be capitalised or something? This time I went to the [typescript docs for basic types](https://www.typescriptlang.org/docs/handbook/basic-types.html) and quickly learned that you only need a suffix of `[]` onto the type of elements expected in your array to declare an array type. Of course I went with `any[]` to just squash this asap, adding to my tech-debt. 10 more errors to go.


* **`Property 'includes' does not exist on type 'number[]'.`** - Come on typescript, now you're just being annoying. This required another tsconfig tweak, adding 'es2017' to the `lib` array under `compilerOptions` (thanks to [this helpful comment](https://github.com/Microsoft/TypeScript/issues/2340#issuecomment-379584805)). What's confusing is that there's `"target": "esnext"` right at the top of the config so you would expect compilation of all the latest and greatest javascript tooling with a name like that. Anyway, 1 more error squashed, 9 more.


* **`Property 'api' does not exist on type 'Home'.`** same same, but different  - `Home` in this case is the name of the main `view` page Vue component. The offending line is within a lifecyle method for the page where I'm trying to initialise a reference to an api client for Google calendar:

	```
	    29 |
	    30 |   public created() {
	  > 31 |     this.api = gapi;
	       |          ^
	    32 |     this.loadGoogleApiClient();
	    33 |   }
	    34 |
	```
	So I added the line `public api = null;` at the top of the class definition and it stopped complaining. Only 4 more left now!

* **`Cannot find name 'gapi'.`** Now it doesn't like the next part of that same line above because `gapi` is initialised directly via a cdn when the page loads:

	```
    30 |
    31 |   public mounted() {
  > 32 |     this.api = gapi;
       |                ^
    33 |     this.loadGoogleApiClient();
    34 |   }
    35 |
	```
	Solution? Screw the cdn, copy and paste the raw code into a .js file of the same name in the assets folder then require that instead for now OR require 'gapi' within the method so it doesn't fuss about finding it when building (this requires setting is as an external module in webpack's config.)

* 3 remaining errors all resolved by setting an object to type `any` using the colon syntax already discovered from the [basic types documentation](https://www.typescriptlang.org/docs/handbook/basic-types.html). *Now* it builds, finally!



## 2. Serve static assets and main app from production dist folder locally with a minimal server.
After all that bruteforcing through foreign error messages this one definitely felt like a doddle.
I popped the following minimal Express script into the root project folder, copied from [this gist](https://gist.github.com/ryanoglesby08/1e1f49d87ae8ab2cabf45623fc36a7fe)

```javascript
const express = require('express')
const path = require('path')
const port = process.env.PORT || 8080
const app = express()

// serve static assets normally
app.use(express.static(__dirname + '/dist'))

// handle every other route with index.html, which will contain
// a script tag to your application's JavaScript file(s).
app.get('*', function(request, response) {
  response.sendFile(path.resolve(__dirname, '/dist/index.html'))
})

app.listen(port)
console.log('server started on port ' + port)
```

## 3. Dockerize the dev and production builds with a multistage Dockerfile and [recommended best practices](https://nodesource.com/blog/containerizing-node-js-applications-with-docker)

Following the steps in the linked guide above was simple enough. I ended up with a Dockerfile that looked like the following sitting in my root project folder:

```Dockerfile
FROM node:11

WORKDIR /home/nodejs/app

# Enable caching of node_modules if possible
COPY package.json .
COPY package-lock.json .
RUN npm ci --production

COPY dist/ .
ENV NODE_ENV production

# Run as a non-root user (see https://github.com/nodejs/docker-node/blob/master/docs/BestPractices.md#non-root-user)
USER node

CMD ["node", "simple_server.js"]
```
I've heard about [multi-stage docker builds](https://cravencode.com/post/docker/nodejs-local-development/) (i.e. one for local development, another for tests, another for the actual deployment etc.) but I'll get back to that once I've got this thing actually deployed.

## 4. & 5. [Spin up dockerized version of app with kubernetes, deploy that to Google Cloud or similar](https://nodesource.com/blog/scalable-nodejs-with-kubernetes-and-google-kubernetes-engine/)

TBC
