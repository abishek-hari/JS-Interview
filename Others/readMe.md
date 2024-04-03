what is the DOM? Differnce between the HTML and DOM?
The DOM(Document Object Model) represents the web page as a tree-like structure that allows javscript to dynamically access and manipuldate the content and structure of a web page.
Html is for reading and writing purpose.

How do you selcect, modify, create and remove DOM elements?s
SELECTING DOM ELEMENTS -
MODIFYING ELEMNTS PROPERTIES -
CREATING & APPENDING ELEMENTS -
REMOVING ELEMENTS -
ADDING EVENTS -

how do you select elements? what are selctors
selectors in js help to get specific elemnts from DOM based on IDs, class names, tage names.
by using all the selectors(by id, name, tagname)

differcence between querySelctor() and querySelctorAll()

- return the first element
- return all the elements

difference between innerHTML and textContent
textcontent - used to assign plain text to the elements.
In simple words it renders the content as plain text
innerHTML - using this the browser interprets the content as HTML and renders it accordingly.
In simple wordsIt renders content as HTML

How to add and remove properties of HTML elemnts in the DOM?
using the setAttributes("data-info", "new value")
using the removeAttribute() for removing.

How to add and remove style from HTML elements in DOM using JS?
using the style.setProperty and using classList.add() and remove() to remove

how do you create element & remove
using the createElement and cloneNode()
createElement is used to create a new elemnt
cloneNode is used to create a clone of the existng element

event delegation
Event Delegation is basically a pattern to handle events efficiently. Instead of adding an event listener to each and every similar element, we can add an event listener to a parent element and call an event on a particular target using the .target property of the event object.
purpose of addeventlistener

event propagation
Propagation refers to how events travel through the Document Object Model (DOM) tree. The DOM tree is the structure which contains parent/child/sibling elements in relation to each other.
The event needs to pass through every node on the DOM until it reaches the end, or if it is forcibly stopped.

Event bubbling and Event Capturing?
Bubbling and Capturing are the two phases of propagation. In their simplest definitions, bubbling travels from the target to the root, and capturing travels from the root to the target.
capturing happen first and bubbling happens second and capture come from top to bottom (document to child) and bubbling is the opposite of that it moves from down to up (child to document)

what is data-atrribute in html
The data-\* attribute gives us the ability to embed custom data attributes on all HTML elements. The stored (custom) data can then be used in the page's JavaScript to create a more engaging user experience

### DOM - DOCUMENT OBJECT MODEL

## AGENDA

- TRAVERSING THE DOM
- DOM MANIPULATION
- EVENT LISTENERS

### TRAVERSING THE DOM

01 - GETTING ELEMENTS

```js
// getElementById
const grandId = document.getElementById("grandparent-id");
changeColor(grand);

// getElementByClassName
const parents = Array.from(document.getElementsByClassName("parent"));
parents.forEach(changeColor);

// QuerySelectors
const grandparent = document.querySelector(".parent");
changeColor(grandparent);

// QuerySelectorAll
const grandparent = document.querySelectorAll(".parent");
grandparent.forEach(changeColor);
```

```js
// Children
const grandId = document.querySelector("#grandparent-id");
const parent = Array.from(grandId.children);
parent.forEach(changeColor);
const parentOne = parent[1];
const children = parentOne.children;
changeColor(children[1]);
```

Instead of using children for all we can use queryselector for the grandparent so we can skip the parent and directly jump into children.

```js
const grandParent = document.querySelector("#grandparent-id");
// For the first child
const child = grandParent.querySelector(".child");
changeColor(child);
// for all children use querySelectorAll()
```

IF WE WANT TO MOVE FROM THE CHILD TO PARENT FROM BOTTOM TO TOP IN THE TREE WE CAN USE PARENTELEMENT

```js
const childOne = document.querySelector("#child-one");
const parent = childOne.parentElement;
const grandParent = parent.parentElement;
changeColor(grandParent);
```

IF WE WANT TO SKIP THE PARENT AND MOVE FROM CHILD TO GRANDPARENT WE CAN USE CLOSET

```js
const childOne = document.querySelector("#child-one");
const grandParent = childOne.closest(".grandparent");
changeColor(grandParent);
```

NEXTELEMETSIBLING & PREVIOUSELEMENTSIBLING

```js
const childOne = document.querySelector("#child-one");
const childTwo = childOne.nextElementSibling;
changeColor(childTwo.previousElementSibling);
```

### DOM MANIPULATION

```js
// ADDING ELEMENTS
/*In appendChild you can append only elements like div, span etc and cannot append strings*/
/*In append you can make all*/
const body = document.body;
body.append("hello world");

// CREATE ELEMENT
const body = document.body;
const div = document.createElement("div");
body.append(div);

// MODIFYING ELEMENT TEXT
const body = document.body;
const div = document.createElement("div");
div.innerText = "wow I have created a text";
div.textContent = "wow I have created a text";
body.append(div);
```

```js
// MODIFYING ELEMENT HTML
const body = document.body;
const div = document.createElement("div");
div.innerHTML = `<strong>wow I have created a text</strong>`;
body.append(div);

// REMOVING ELEMENTS
const body = document.body;
const div = document.querySelector("div");
const spanHi = document.querySelector(".hi");
const spanBye = document.querySelector(".bye");

spanBye.remove();
div.removeChild(spanHi);
```

```js
// MODIFYING ELEMENT ATTRIBUTES
// getAttributes & setAttributes & removeAttributes
 const div = document.querySelector("div");
const spanHi = document.querySelector(".hi");
const spanBye = document.querySelector(".bye");

console.log(spanHi.getAttribute("class"));
// another method
console.log(spanHi.title);

console.log(spanBye.setAttribute("class", "hello"));
// another method
console.log((spanBye.title = "byess"));

spanHi.removeAttribute('class')

// MODIFYING DATA ATTRIBUTES
const spanHi = document.querySelector(".hi");
console.log(spanHi.dataset.test);

// MODIFYING ELEMENT CLASSES
 const spanHi = document.querySelector(".hi");
spanHi.classList.add("hello");
spanHi.classList.remove("hi2");
spanHi.classList.toggle("h3"); */

// MODIFYING ELEMENT STYLE
const spanHi = document.querySelector(".hi");
spanHi.style.backgroundColor = "red";
```

### EVENT LISTENERS

```js
const grandParent = document.querySelector(".grandparent");
const parent = document.querySelector(".parent");
const child = document.querySelector(".child");

grandParent.addEventListener(
  "click",
  (e) => {
    console.log("grandparent capture");
  },
  { capture: true }
);
grandParent.addEventListener("click", (e) => {
  console.log("grandparent bubble");
});

parent.addEventListener(
  "click",
  (e) => {
    e.stopPropagation();
    console.log("parent capture");
  },
  { capture: true }
);
parent.addEventListener("click", (e) => {
  console.log("parent bubble");
});

child.addEventListener(
  "click",
  (e) => {
    console.log("child capture");
  },
  { capture: true }
);
child.addEventListener("click", (e) => {
  console.log("child bubble");
});

document.addEventListener(
  "click",
  (e) => {
    console.log("document capture");
  },
  { capture: true }
);
document.addEventListener("click", (e) => {
  console.log("document bubble");
});
```

- EVENT BUBBLING AND CAPTURING
  capturing happen first and bubbling happens second and capture come from top to bottom (document to child) and bubbling is the opposite of that it moves from down to up (child to document)

  capture is the third parameter in the addEventListener

<!-- ERROR HANDILING -->

01 - what is error handling

```js
try{
  const result = someUndefinedVariable + 10;
  console.log(result)
}catch(error){
  console.log('An error occured': error.message)
}
```

02 - what is the role of finally block in js

```js
try{
  const result = someUndefinedVariable + 10;
  console.log(result)
}catch(error){
  console.log('An error occured': error.message)
}finally{
   console.log('Finally Executed')
}
// finally, block is used to execute some code irrespective of error.
// finally is used if error occured or not it will always return
```

03 - what is the purpose of the throw statement in js?
The throw statement stops the execution of the current function and passes the error to the catch block of calling function.

04 - what is Error propagation in js?

05 - what are the different types of errors in js
