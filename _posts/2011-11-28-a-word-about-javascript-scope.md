---
layout: post
title: Post Mortem - A word about JavaScript Scope
---
This is a post from my old blog. I've seen that this still gets hits on occasion, so I thought I'd bring it back from the archives.

**Before we get started, all of this example code, as well as test runs for it, can be found [here](http://imgineme.com/jsscope.html)**

I've seen expert programmers get a little confused about what exactly is in scope at any given time in JavaScript. It is certainly a unique language in the fact that it will let you do just about whatever you'd like to sometimes. There is quite a fair amount of material on this issue, and you can just Google "js scoping" to find some, but I wanted to cover it because I feel it a fundamental place to start, especially if you are coming from another language.

So, I'll start off with a fairly simple example:

## Basic Scope

```javascript
var a = &quot;This is a&quot;;

function scope1() {
	var b = &quot;This is b&quot;;
	// Print a
	document.writeln(a);
	// Print b
	document.writeln(b);
}

// Run the function
scope1();
```

The above will output "This is a" and then "This is b". Fairly simple. Variable a is declared outside the scope of a function, so it is global, while b is declared in the function. If I were to try and access b outside the function, I would get an [undefined](https://blog.udemy.com/javascript-tutorial-learn-the-basics/#10_6) variable.

Now, onto some more complex examples:

## Global Vs Local

```javascript
var a = &quot;Global&quot;;

function scope1() {
	var a = &quot;Local&quot;;

	// Print Global
	document.writeln(this.a);
	// Print Local
	document.writeln(a);
}

// Run the function
scope1();
```

Now, if you are familiar with other languages, this may look a little odd. The global variable is referenced with this, and the local is accessed without. This actually has to do with the fact that javascript assigns all global variables to the window object, and at any given point, unless inside an object, this is a reference to the window object. So, this.a is equivalent to saying window.a

## Object Scope

First, if you haven't read up on JavaScript objects, you [probably should](https://blog.udemy.com/javascript-tutorial-learn-the-basics/#15).

```javascript
// Create a new Object
var a = new Object();
// Assign a public variable
a.public = &quot;Public&quot;;

// Print the public variable
document.writeln(a.public);
// Show static variable is not set (outputs undefined)
document.writeln(a.static);

// Assign a static variable to all objects of type Object using the keyword prototype
Object.prototype.static = &quot;Static&quot;;

// Assign a nonstatic variable to a type of object
Object.nonStatic = &quot;Non-Static&quot;;

// Print the static variable using Object a
document.writeln(a.static);
// Show nonstatic variable did not get assigned (outputs undefined)
document.writeln(a.nonStatic);
// Print the nonstatic variable from the generic Object
document.writeln(Object.nonStatic);
```

This example is actually a fairly simple one for most programmers to wrap their minds around. Coming from Java, I got introduced to the static variable pretty quickly. In JavaScript, however, if you want to define a static variable, you have to use the prototype notation.

## Custom Object Scope

```javascript
// Define a custom object
function b() {
	// Declare public variable
	this.public = &quot;B Public&quot;;
	// Declare protected variable
	var nonPublic = &quot;B Protected&quot;;

	// Declare public function
	this.protectedAccess = function () {
		return nonPublic;
	};
}

// Create a new instance of the object type b
var bHold = new b();
// Print public variable
document.writeln(bHold.public);
// Print protected variable (will print undefined)
document.writeln(bHold.nonPublic);
// Print protected variable via function
document.writeln(bHold.protectedAccess());
```

For those who know about JavaScript object definition, this probably makes a lot of sense. For those who do not, this is probably completely confusing. In strictly defined languages like Java and C#, you define a custom object type with the keyword class, and a lot of time will separate it out into its own file. In JavaScript, however, you define a class the same way you would define a function. The differences being that the this keyword (covered more below) will refer the the object, and when you create the new object, you do so by call new function_name().

Now, once we have the object defined, this again turns into a simple example of public vs private variables. Any variables defined with the this. notation will be available as public variables. Any variables defined without that will be available only within the scope of the object. And, especially since JavaScript is such an open and forgiving language, having private variables is certainly something that is useful.

## this Keyword
### HTML:

```html
<input type="button" value="Print Button" name="The Button" id="test5Button" /><input type="button" value="Print Object" id="test5Obj" />
```

### JavaScript:

```javascript
function button() {
	// Set the Objects Name
	this.name = &quot;The Object&quot;;

	// Get the pre area to attach the results to
	var pre = document.getElementById(&#039;pre5&#039;);

	// Get the Print Button Button
	var button = document.getElementById(&#039;test5Button&#039;);
	// Set the onclick handle
	button.onclick = function (event) {
		// Print The Button
		pre.innerHTML = this.name;
		// Prevent submit in some browsers
		event.preventDefault();
	};

	// Get the Print Object Button
	var obj = document.getElementById(&#039;test5Obj&#039;);
	// A Self Reference to have access to this object
	var SelfReference = this;
	obj.onclick = function (event) {
		// Print The Object
		pre.innerHTML = SelfReference.name;
		event.preventDefault();
	}
}
// Create a new instance of the button to initialize the above
var b = new button();
```

The above is a lot less complicated then it looks at first glance, and it is closer to JavaScript you may actually see in real world situations. I define a new custom object type button, and then I set its name. All of the code within this function acts as initialization code run when the object is first created. I go through both of the given HTML buttons, and I add onclick events to each of them.

For the first onclick event, I use the this keyword to access the button. I then print the associated name for that button in the box. For the second onclick event, it is a little more complicated. I picked up this trick a while back so as to not loose a reference to the object once you are inside a function where this is in a different scope. The trick is that even though this gets reassigned, you can still access other variables from within that scope, so you can set a variable equal to the this reference to the object to retain the scope. Basically, I assign a second pointer to the object that I'm in so that when the first pointer is reassigned, I still have access to its original value. This is a nifty trick that you will see throughout my code.

Hopefully this gave people a new insight into JavaScript scoping. If you have any questions, feel free to ask in the comments.
