# Javascript DOM Manipulation & Events

### Lesson Objectives
* Describe what the DOM is
* Use JS to find elements in the DOM
* Use JS to manipulate them
* Use JS to listen to events


##What is the DOM?

It's the HTML that you wrote, when it is parsed by the browser. After it is parsed - it is known as the DOM. It can be different to the HTML you wrote, if the browser fixes issues in your code, if javascript changes it etc.

_How do we use it?_

The document object gives us ways of accessing and changing the DOM of the current webpage.

_General strategy:_

Find the DOM node using an access method
Store it in a variable
Manipule the DOM node by changing its attributes, styles, inner HTML, or appending new nodes to it.

####Get Element by ID
````javascript
// The method signature:
// document.getElementById(id);

// If the HTML had:
// <img id="mainpicture" src="http://placekitten.com/200/300">
// We'd access it this way:
var img = document.getElementById('mainpicture');

// DON'T USE THE HASH!
````

####Get Elements by Tag Name
````javascript
// The method signature:
// document.getElementsByTagName(tagName);

// If the HTML had:
<li class="catname">Lizzie</li>
<li class="catname">Daemon</li>
// We'd access it this way:
var listItems = document.getElementsByTagName('li');
for (var i =0; i < listItems.length; i++) {
  var listItem = listItems[i];
}
````
####Query Selector and Query Selector All
````javascript
// The HTML5 spec includes a few even more convenient methods.
// Available in IE9+, FF3.6+, Chrome 17+, Safari 5+:

document.getElementsByClassName(className);
var catNames = document.getElementsByClassName('catname');
for (var i =0; i < catNames.length; i++) {
  var catName = catNames[i];
}

// Available in IE8+, FF3.6+, Chrome 17+, Safari 5+:
document.querySelector(cssQuery);
document.querySelectorAll(cssQuery);
var catNames = document.querySelectorAll('ul li.catname');
````
Remember, some of these methods return arrays and some return single things!

Will return Single Elements
````javascript
getElementById()
querySelector() * returns only the first of the matching elements
  var firstCatName = document.querySelector('ul li.catname');
Will return an Array
````
Others return a collection of elements in an array:
````javascript
getElementsByClassName()
getElementsByTagName()
querySelectorAll()
  var catNames = document.querySelectorAll('ul li.catname');
  var firstCatName = catNames[0];
````

##Changing Attributes with Javascript

You can access and change attributes of DOM nodes using dot notation.

We can change the src attribute of an immage this way:
````javascript
var oldSrc = img.src;
img.src = 'http://placekitten.com/100/500';

// To set class, use the property className:
img.className = "picture";
````
####Changing Styles with Javascript

You can change styles on DOM nodes via the style property.

If we had this CSS:
````css
body {
  color: red;
}
````
We'd run this JS:
````javascript
var pageNode = document.getElementsByTagName('body')[0];
pageNode.style.color = 'red';
````
CSS property names with a "-" must be camelCased and number properties must have a unit:
````javascript
//To replicate this:

// body {
//   background-color: pink;
//   padding-top: 10px;
// }
pageNode.style.backgroundColor = 'pink';
pageNode.style.paddingTop = '10px';
Changing an elements HTML
````
Each DOM node has an innerHTML property with the HTML of all its children:
````javascript
var pageNode = document.getElementsByTagName('body')[0];
````
You can read out the HTML like this:
````javascript
console.log(pageNode.innerHTML);

// You can set innerHTML yourself to change the contents of the node:
pageNode.innerHTML = "<h1>Oh Noes!</h1> <p>I just changed the whole page!</p>"

// You can also just add to the innerHTML instead of replace:
pageNode.innerHTML += "...just adding this bit at the end of the page.";
````
####DOM Modifying

The document object also provides ways to create nodes from scratch:
````javascript
document.createElement(tagName);

document.createTextNode(text);

document.appendChild();

var pageNode = document.getElementsByTagName('body')[0];

var newImg = document.createElement('img');
newImg.src = 'http://placekitten.com/400/300';
newImg.style.border = '1px solid black';
pageNode.appendChild(newImg);

var newParagraph = document.createElement('p');
var paragraphText = document.createTextNode('Squee!');
newParagraph.appendChild(paragraphText);
pageNode.appendChild(newParagraph);
````

##Events

####Adding Event Listeners

In IE 9+ (and all other browsers):
````javascript
domNode.addEventListener(eventType, eventListener, useCapture);

// HTML = <button id="counter">0</button>

var counterButton = document.getElementById('counter');
var button = document.querySelector('button')
button.addEventListener('click', makeMadLib);

var onButtonClick = function() {
    counterButton.innerHTML = parseInt(counterButton.innerHTML) + 1;
};
counterButton.addEventListener('click', onButtonClick, false);
````
####Some Event Types

The browser triggers many events. A short list:

mouse events (MouseEvent): 
* mousedown, mouseup , click, dblclick, mousemove, mouseover, mousewheel , mouseout, contextmenu

touch events (TouchEvent): 
* touchstart, touchmove, touchend, touchcancel

keyboard events (KeyboardEvent): 
* keydown, keypress, keyup

form events: 
* focus, blur, change, submit

window events: 
* scroll, resize, hashchange, load, unload

Getting Details from a Form
````javascript
// HTML
// <input id="myname" type="text">
// <button id="button">Say My Name</button>

var button = document.getElementById('button');
var onClick = function(event) {
    var myName = document.getElementById("myname").value;
    alert("Hi, " + myName);
};
button.addEventListener('click', onClick);
````
####Window

When you run JS in the browser, it gives you the window object with many useful properties and methods:
````javascript
window.location.href; // Will return the URL
window.navigator.userAgent; // Tell you about the browser
window.scrollTo(10, 50);
````
Lots of things that we have been using are actually a part of the window object. As the window object is the assumed global object on a page.
````javascript
window.alert("Hello world!"); // Same things
alert("Hello World!");

window.console.log("Hi"); // Same things
console.log("Hi");
````
####Animation in JS

The standard way to animate in JS is to use these 2 window methods.

To call a function once after a delay:
````javascript
window.setTimeout(callbackFunction, delayMilliseconds);
````
To call a function repeatedly, with specified interval between each call:
````javascript
window.setInterval(callbackFunction, delayMilliseconds);
````
Commonly used to animate DOM node attributes:
````javascript
var makeImageBigger = function() {
  var img = document.getElementsByTagName('img')[0];
  img.setAttribute('width', img.width+10);
};
window.setInterval(makeImageBigger, 1000);
````
####Animating Styles

It's also common to animate CSS styles for size, transparency, position, and color:
````javascript
var img = document.getElementsByTagName('img')[0];
img.style.opacity = 1.0;
window.setInterval(fadeAway, 1000);
var fadeAway = function() {
  img.style.opacity = img.style.opacity - .1;
};

// Note: opacity is 1E9+ only (plus all other browsers).
//
var img = document.getElementsByTagName('img')[0];
img.style.position = 'absolute';
img.style.top = '0px';
var watchKittyFall = function() {
  var oldTop = parseInt(img.style.top);
  var newTop = oldTop + 10;
  img.style.top = newTop + 'px';
};

window.setInterval(watchKittyFall, 1000);
// Note: you must specify (and strip) units.
Stopping an Animation
````
To stop at an animation at a certain point, store the timer into a variable and clear with one of these methods:
````javascript
window.clearTimeout(timer);
window.clearInterval(timer);
var img = document.getElementsByTagName('img')[0];
img.style.opacity = 1.0;

var fadeAway = function() {
  img.style.opacity = img.style.opacity - .1;
  if (img.style.opacity < .5) {
    window.clearInterval(fadeTimer);
  }
};
var fadeTimer = window.setInterval(fadeAway, 100);
````