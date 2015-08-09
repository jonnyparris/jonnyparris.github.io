---
layout: post
title:  "Why are js closures called closures?"
date:   2015-07-31 10:49
categories: learning-code naming
excerpt: <p>Attempting to link naming with definition with some imagination</p>
---

I find it much easier to remember definitions of concepts and terms if I can somehow link it to an explanation or story behind its name. My naming stories may not always be historically accurate or especially exciting but they work for me so maybe you'll find them useful too.
If you're here, I'm assuming that you already understand the concept but you're looking for a way to remember/explain/imagine why it's been named.

### Why are js closures called *closures*?

A quick "define closure" google reveals the following:

__noun__ __*1. an act or process of closing something, especially an institution, thoroughfare, or frontier, or of being closed.*__

In javascript, a closure describes a function that refers to variables that would otherwise be garbage-collected/killed/__*closed down*__ if that function didn't exist. I.e. "If it weren't for me you'd be dead by now kiddo" says the function to the fugitive variable whose being maintained outside the scope of its definition.

__You can imagine that a closure is a function that's promising to *close* the scope of these 'deathrow variables'__ as soon the function itself *closes*.

E.g. without closure:

{% highlight js linenos %}
function Batman () {
  var privateVariable = "knickers" // <== deathrow variable
} // <== the executioner scope-closing curly bracket

var ben = new Batman()
return ben.privateVariable // => undefined
// because privateVariable was 'closed' by the closing curly bracket on line 3.
{% endhighlight %}

with closure:

{% highlight js linenos %}
function Batman () {
  var privateVariable = "knickers"

  // here's the closure function
  this.getPreference = function() {
    return privateVariable
  }
}

var ben = new Batman()
return Ben.getPreference() // => "knickers"
{% endhighlight %}


Make sense? Lemme know below.
