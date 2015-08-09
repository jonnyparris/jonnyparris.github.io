---
layout: post
title:  "Why is it called dependency injection?"
date:   2015-07-29 12:18
categories: learning-code naming
excerpt: <p>Attempting to link naming with definition, using some imagination</p>
---

I find it much easier to remember definitions of concepts and terms if I can somehow link it to an explanation or story behind its name. My naming stories may not always be historically accurate or especially exciting but they work for me so maybe you'll find them useful too.

### Why is dependency injection called dependency *injection*?

Instead of having an object dependency (object that your your new class needs) baked into the definition of your class like this (javascript):

{% highlight js %}
var ExampleClass = function() {
  this.classVariable = SomeDependentClass.new()
}
{% endhighlight %}

you __**inject**__ that dependency into your class via its constructor arguments like this:

{% highlight js %}
var ExampleClass = function(injectedObject) {
  this.classVariable = injectedObject
}
{% endhighlight %}

That wasn't very intuitive for me the first time I came across the term...so I promptly forgot it until I had to deal with it again while getting acquainted with AngularJS.

Anything amiss? Comment/feedback is always welcome.
