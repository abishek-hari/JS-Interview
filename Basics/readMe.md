# FRONTEND DEVELOPMENT

Frontend development refers to the process of building and maintaining the user interface (UI) of a website or web application. It involves creating the visual elements that users interact with directly on their browsers. Frontend developers use a combination of HTML, CSS, and JavaScript to structure content, style elements, and add interactivity.
In essence, frontend development focuses on everything that users see, touch, and interact with on a website

### AGENDA

- JAVASCRIPT
- VARIABLES & DATATYPES
- TYPE COERICION
- VALUE VS REFERENCE
- SHALLOW & DEEP COPY

# JAVASCRIPT BASICS

Javascript is a dynamic typed single-threaded languange
JavaScript is a versatile and widely-used programming language that enables interactive and dynamic functionality on web pages
In September 1995, Bredan Eich, a programmer at NetScape developed a language.It was called Mocha, then livescript and later renamed it as JavaScript

### Advantages and Disadvantages

- Advantages

1. Versatility: JavaScript can be used for both front-end (client-side) and back-end (server-side) development, making it a versatile language.
   Example: A company wants to develop a new cross-platform mobile application. By using a technology like React Native, developers can write the application's codebase in JavaScript, allowing them to use a single codebase for both iOS and Android platforms, reducing development time and costs.

2. Interactivity: It enhances the interactivity of web pages, creating dynamic and engaging user experiences.
   Example: A modern e-commerce website employs JavaScript to create features like dynamic product filters, real-time price calculations, and interactive shopping carts. These features enhance the user experience, making it easier for customers to find and purchase products.

3. Wide Adoption: JavaScript is widely supported by all major web browsers, making it a standard for web development.
   Example: A startup company decides to build its web application using JavaScript due to its widespread support in all major web browsers. This ensures that the application will be accessible to a wide range of users, regardless of the browser they use.

4. Large Ecosystem: A vast ecosystem of libraries and frameworks (e.g., React, Angular, and Vue) simplifies development and offers pre-built solutions.
   Example: A web developer needs to add a complex data visualization component to a project. Instead of building it from scratch, they can utilize a JavaScript library like D3.js or Chart.js, which provides pre-built solutions for creating interactive charts and graphs. This saves development time and effort.

- Disadvantages

1. Browser Compatibility: Cross-browser compatibility issues can arise, requiring testing and additional code for consistency.
   Example: If you develop a web application that works perfectly in one browser but breaks in another, you're facing a browser compatibility issue. For instance, a feature may work seamlessly in Google Chrome but may not function as expected in Internet Explorer. This often requires additional code and testing to make the application consistent across different browsers.

2. Security Risks: JavaScript can be vulnerable to security threats like Cross-Site Scripting (XSS) if not properly secured.
   Example: Let's say you have a web form that allows users to input text. If you don't properly sanitize or validate the input, an attacker can insert malicious code into the form, and this code could be executed on other users' browsers. This is a real security risk, and it can lead to data breaches and unauthorized actions on the website.

3. Performance: Inefficient coding practices can lead to slow page loading times and suboptimal performance.
   Example: Consider a web page with complex animations and many images that are not optimized. In this case, the page can load slowly, especially on mobile devices or slow internet connections. Slow performance can lead to a poor user experience, with users waiting for the page to load or experiencing janky animations.

4. Single-Threaded: JavaScript is single-threaded, which can lead to performance bottlenecks in CPU-intensive operations.
   Example: Suppose you're developing a web application that performs heavy computational tasks, such as rendering 3D graphics or complex data analysis. JavaScript is single-threaded, so if one task is running for a long time, it can block the entire application, making it unresponsive. This can result in users experiencing delays and unresponsiveness while using the application.

### FEATURES

- lightweight, interpreted programming language
  High-level Language:
- JavaScript is a high-level, interpreted language, making it accessible for developers.
  Dynamic Typing:
- Variables are dynamically typed, the type of the variable can change at runtime.
  Asynchronous Programming:
- Supports asynchronous operations using callbacks and promises.

### Java vs Javscript

- javascript is an object-oriented scripting language
- Java is an object-oriented programming language.

- JavaScript applications are meant to run inside a web browser.
- Java applications are generally made for use in operating systems and virtual machines.

- JavaScript does not need compilation before running the application code.
- Java source code needs a compiler before it can be ready to run in realtime.

### Variables

Variable are used to store data.To create a variable we can use the let and const keyword

### Data types

Data types describe the different types of data that we're gonna be working with and storing in variables. It associates the declared variable (or item) with a particular type so that the compiler can perform operations in an organized manner.

There are mainly two types of data types in JavaScript:

### Primitive data types.

primitive datatypes are immutable data types.once a primitive data type is created we cannot modify it. primitive datatypes are compared by its value.

### Non-primitive data types.

Non-primitive data types are modifiable or mutable.we can modify the value of non-primitive data types after it gets created. compared by reference instead of value.

### static and dynamic languages

static languages: when we declare a variable the type of that variable is set and cannot be changed in future
Dynamic language : the type of the variable can change at runtime.

### primitive datatype :

# string literal

- It represents a series of characters and is written with quotes

```js
let name = "abishek";
```

# number literal

- It represents a number and can be written with or without decimals

```jss
let age = 20;
```

# boolean literal

- It represents a logical entity and can have only two values : true or false.

```js
let isApproved = false;
```

# undefined

undefined means a variable has been declared but has not yet been assigned a value.

```js
let fistLetter = undefined;
```

# null

null is a special value that represents an empty or unknown value or absence of value. For example, let number = null; it indicates that the number variable is empty at the moment and may have a value later.

```js
let selectColor = null;
```

### Non-primitive datatype :

# OBJECT:

An object in JavaScript is a composite data type that allows you to store key-value pairs. It is a collection of properties, where each property has a key and a corresponding value.

How to create an Object
You can create an object using object literal notation, which involves enclosing key-value pairs within curly braces {}

```js
let person = {
  name: "John",
  age: 30,
  occupation: "Developer",
};
```

# ARRAY:

An array in JavaScript is a special type of object used for storing and manipulating ordered lists of values. Unlike objects, arrays use numeric indices to access elements, and they are particularly useful for working with collections of similar or sequential data.

How to Create an Array:
You can create an array using array literal notation by enclosing elements within square brackets []

```js
let numbers = [1, 2, 3, 4, 5];
```

# NAN

NAN property represents the “Not-a-Number” value and it is a property of the global object.It indicates a value that is not a legal number.typeof of NaN will return a Number.

Why does typeof NaN return “number”?
The reason typeof NaN returns 'number' in JavaScript is because it is based on IEEE 754 floating-point standard, which JavaScript follows for numeric operations. In the IEEE 754 standard, the NaN value is considered a numeric value. so when a mathematical operation results in an undefined or unrepresentable value, like dividing zero by zero, the result is NaN.
(Institue of Eletrical and Electronic Engg)

There are several ways in which NaN can happen:

- Division of zero by zero
- Dividing an infinity by an infinity
- Multiplication of an infinity by a zero
- A string divided by number will be NAN

**A number divided by zero will be Infinity**

### TYPE COERCION

Type coercion is the automatic or implicit conversion of values from one data type to another.
It takes place when the operands of an expression are of different data types.

```js
const x = "10";
const y = 10;
```

# implicit type coercion

Implicit type coercion, also known as type coercion or type conversion, occurs when the JavaScript engine automatically converts one data type to another

```js
const res1 = x + y; // 1010 implicit
```

# explicit type coercion

Explicit type coercion, also known as type casting, is the conversion of a value from one data type to another by using explicit language syntax or functions.

```js
const res2 = Number(x) + y; // 20 explicit
```

# String Coercion

If string and number are added it will convert into string

```js
const xy = "10" + 5; //105
console.log(xy);
```

If string and number are - , \*, /, % it will convert into number

```js
const yx = "10" - 5; // 5
console.log(yx);
```

# Boolean coercion

when performing arithmetic operations involving boolean values (true and false), they are implicitly converted to numbers. In JavaScript, true is equivalent to 1, and false is equivalent to 0.

```js
const zy = 5 + true; // true is implicitly converted to 1
const zx = 10 + false; // false is implicitly converted to 0

console.log(zx, zy); // Outputs: 10 6

// Another Example

var x = 0;
var y = 23;

if (x) {
  console.log(x);
} // The code inside this block will not run since the value of x is 0(Falsy)

if (y) {
  console.log(y);
} // The code inside this block will run since the value of y is 23 (Truthy)
```

Logical operators in javascript, unlike operators in other programming languages, do not return true or false. They always return one of the operands.

OR ( | | ) operator - If the first value is truthy, then the first value is returned. Otherwise, always the second value gets returned.

AND ( && ) operator - If both the values are truthy, always the second value is returned. If the first value is falsy then the first value is returned or if the second value is falsy then the second value is returned.

```js
// Example 1:
const result1 = true || false;
console.log(result1); // Output: true
// In this case, the first value (true) is truthy, so it is returned.

// Example 2:
const result2 = 0 || "Hello";
console.log(result2); // Output: Hello
// Here, the first value (0) is falsy, so the second value ('Hello') is returned.

// Example 1:
const result3 = true && "World";
console.log(result3); // Output: World
// Both values are truthy, so the second value ('World') is returned.

// Example 2:
const result4 = false && "Goodbye";
console.log(result4); // Output: false
// The first value (false) is falsy, so it is returned.

// Example 3:
const result5 = "Hi" && null;
console.log(result5); // Output: null
// The second value (null) is falsy, so it is returned.
```

```js
var x =  220;
var y = "Hello";
var z = undefined;

x | | y    // Returns 220 since the first value is truthy

x | | z   // Returns 220 since the first value is truthy

x && y    // Returns "Hello" since both the values are truthy

y && z   // Returns undefined since the second value is falsy

if( x && y ){
  console.log("Code runs" ); // This block runs because x && y returns "Hello" (Truthy)
}

if( x || z ){
  console.log("Code runs");  // This block runs because x || y returns 220(Truthy)
}
```

# Equality Coercion

== ===
double equal check the value of both but the triple equal checks both the value and the datatype

```js
// "==" operator checks the value of both
var a = 12;
var b = "12";
a == b; // Returns true because both 'a' and 'b' are converted to the same type and then compared. Hence the operands are equal.
```

```js
// "===" the triple equal checks both the value and the datatype
var a = 226;
var b = "226";

a === b; // Returns false because coercion does not take place and the operands are of different types. Hence they are not equal
```

### Truthy and Falsy Value

A value is considered "truthy" if, when evaluated in a boolean context, it is treated as true

A value is considered "falsy" if, when evaluated in a boolean context, it is treated as false

- The boolean value false.
- The number 0.
- An empty string ("").
- null.
- undefined.
- NaN (Not-a-Number).

```js
let truthyExample = "Hello"; // truthy
let falsyExample = 0; // falsy

if (truthyExample) {
  console.log("Truthy!"); // This will be executed
}

if (!falsyExample) {
  console.log("Falsy!"); // This will be executed
}
```

### Passed by Value vs Passed by reference

# Passed By Value

'passed by value' is when a variable is passed to a function or assigned to another variable, a copy of its actual value is made. Any changes made to the parameter or the new variable inside a function do not impact the original variable outside of that function.

```js
let a = 10;
let b = a; // 'b' receives a copy of the value of 'a'
b = b + 5; // Changes to 'b' do not affect 'a'
```

# Passed By Reference

'Passed By Reference' is when a variable is passed to a function or assigned to another variable, the memory address or reference of that variable is passed. Consequently, any modifications made to the parameter or the new variable directly affect the original variable.

```js
let arr1 = [1, 2, 3];
let arr2 = arr1; // 'arr2' receives the reference to the memory of 'arr1'
arr2.push(4); // Changes to 'arr2' also impact 'arr1'
```

Important Points:

- JavaScript is "passed by value" for primitive types and "passed by reference" for objects (including arrays).

- Though it may seem like objects are passed by reference, they are actually passed by value. However, the value being passed is a reference to the object's memory location.

## Shallow copy vs Deep copy

There are two ways to clone an object in Javascript:

Shallow copy: means that only the first level of the object is copied. Deeper levels are referenced.
Deep copy: means that all levels of the object are copied. This is a true copy of the object.

# Shallow Copy

A shallow copy of an object or array involves duplicating the top-level structure while maintaining references to the original nested objects or arrays. Modifications to the nested elements in the shallow copy will impact the original object or array

```js

let originalArray = [1, 2, [3, 4]];

// Creating a shallow copy using slice() for arrays
let shallowCopy = originalArray.slice();

// Modifying the nested array in the shallow copy
shallowCopy[2][0] = 99;

console.log("Original Array:", originalArray);
console.log("Shallow Copy:", shallowCopy);


Original Array: [1, 2, [99, 4]]
Shallow Copy: [1, 2, [99, 4]]

```

# Deep Copy

A deep copy of an object or array entails creating a new structure and recursively duplicating all nested elements. This results in an entirely independent copy with no shared references to the original object or array.

```js
let originalObject = { a: 1, b: { c: 2, d: 3 } };

// Creating a deep copy using JSON.parse() and JSON.stringify() for objects
let deepCopy = JSON.parse(JSON.stringify(originalObject));

// Modifying the nested object in the deep copy
deepCopy.b.c = 99;

console.log("Original Object:", originalObject);
console.log("Deep Copy:", deepCopy);

Original Object: { a: 1, b: { c: 2, d: 3 } }
Deep Copy: { a: 1, b: { c: 99, d: 3 } }

```

# CONDITIONAL STATEMENT

A conditional statement in programming is a construct that allows the execution of different code blocks based on whether a specified condition evaluates to true or false. In JavaScript, common conditional statements include if, else if, and else. They provide a way to control the flow of the program based on certain conditions

```js
let number = 10;

if (number > 0) {
  console.log("The number is positive.");
} else if (number < 0) {
  console.log("The number is negative.");
} else {
  console.log("The number is zero.");
}
```

# LOOPS

Loops in programming are structures that allow a set of instructions to be repeated multiple times. They are essential for performing repetitive tasks efficiently. In JavaScript, common types of loops include for, while, and do-while

```js
let fruits = ["apple", "banana", "orange"];

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```
