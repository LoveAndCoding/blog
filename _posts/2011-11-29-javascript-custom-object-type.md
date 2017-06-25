---
layout: post
title: Post Mortem: JavaScript Custom Object Types
---
Another revived post from my old blog.

So, this one I'm going to make a fair bit smaller then the last couple. In my last post, I used some notation for creating a custom object that may have confused some who are unfamiliar with the language, or are just getting started with it. So, briefly I just wanted to go over it again, and dedicate a post entirely to the topic.

## Defining

First things first, a custom object type in JavaScript is defined using the same conventions you use to create a new function. There are a few differences in the notations from there, but that is first and foremost. From there, when you are creating a new instance of that object, you use the keyword new, just like you do in other languages. Here's a sample:

```javascript
function obj_type() {}

var obj = new obj_type();
```
## Methods
As you can see, its a pretty simple notation when it is completely stripped down. Now let's define some methods for it. We actually have a few options for how we do this. We can either prototype the methods in, or we can define them like we would variables. Functionally, they act the same, but I, personally, prefer the latter. A lot of people, however, prefer to use the prototyping functions. Both are illustrated below.
**Prototype:**
```javascript
function world() {}

world.prototype.sayHi = function () {
	alert("Hello World!");
};
```

**Inside:**

```javascript
function world(){

	this.sayHi = function () {
		alert("Hello World!");
	};

}
```

I use the inside method for two reasons. One, I have become used to using it because GreaseMonkey does not allow prototyping onto existing objects without using the unsafeWindow object (or at least that used to be the case; I haven't tried in a while). Two, coming from a defined language like Java, I am used to all class definitions being in one contained spot. I feel it is easier to read from an outside prospective.

*Note that functions here are considered variable assignments and it is therefore syntactically correct to put a semi-colon after the last } defining the function.*

## Variables

Variables' scope is discussed in [my post on scoping](http://design.imgineme.com/2011/11/28/a-word-about-javascript-scope/) and JavaScript, but I'll review it here real fast. Public Variables are defined with the this keyword, and private variables are defined with just the var keyword:

```javascript
function vars() {
	this.a = "This is public";
	var b = "This is private";
}
```

## Parameters &amp; Constructor Actions

Parameters are passed in just like they are to other functions. Constructor actions are any actions within the definition that would be executed if the function was called. This can be used to define initial values for variables, or to do things that need to be completed upon initialization. For example:

```javascript
function mathed(a, b) {
	this.val1 = a;
	this.val2 = b;

	this.added = a + b;
	this.subtracted = a - b;
	this.rSubtracted = b - a;

	this.multiplied = a * b;
	this.divided =  a / b;
	this.rdivided = b / a;

	alert(a + " and " + b + " have been mathed");
}
```

The above will do the calculations at each step and then alert the message. The object will then contain all of these values stored. You may notice that if a or b change, these values are not update, but I'll leave that as a problem for you to solve.
