# SCOPE AND EXECUTION

## AGENDA

1. Hoisting
   1.1 undefined vs not defined
2. ScopeChain
   2.1 scope
   2.2 Lexical Environment
3. Let & Const
   3.1 Temporal Dead Zone
   3.2 Syntax Error
   3.3 Reference Error
   3.4 Type Error
4. Block Scope
   4.1 shadowing of variable

## Hoisting

**JavaScript** hoisting occurs during the creation phase of the execution context that moves the variable and function declarations to the top of the script.

The JavaScript engine hoists the variables declared using the let keyword, but it doesn’t initialize them as the variables declared with the var keyword.
The JavaScript engine doesn’t hoist the function expressions and arrow functions.

Suppose you declare a variable, let's say 'var a,' and initialize its value as 10. If we attempt to access 'a' before its declaration, the result will be undefined. During the creation phase, memory is allocated for variables, and they are assigned a special keyword called 'undefined.' Functions, on the other hand, are assigned to the entire {block} of code that is created, allowing us to access the values of the function even before their actual declarations.

```js
a();
b();
console.log(xz);
var xz = 1;

function a() {
  const xy = 10;
  console.log(xy);
}

function b() {
  var x = 100;
  console.log(x);
}

// Output
10;
100;
undefined;
```

**Declaration**
Declaration declares the creation of variables and functions.

**Initialization**
Initialization assigns initial values to variables

**Invocation**
Invocation executes a piece of code

**statement**
A JavaScript statement is a piece of code used to instruct the computer on an action to execute.
JavaScript statements often start with a statement identifier to identify the JavaScript action to be performed.
Statement identifiers are reserved words and cannot be used as variable names (or any other things).
For eg: let bestColor; It instruct the computer to create a let variable named bestColor

**Let & const** are allocated memory but in different memory space than Global object
You cannot access these let & const declaration before you have assign a value to it

**temporal dead zone** is time since the let & const variable was hoisted and till initialize some value
whenever you try to access a varibale inside a temporal dead zone it will give you refference error

**Undefined and not defined**

- Undefined
  undefined means a variable has been declared but has not yet been assigned a value.

- Not defined
  The not defined indicates that a varibale does not exist

### Scope Chain

#### Scope

**THE SCOPE**

scope means where you can access a specfic variable or function in a code

1. what is the scope of the variable
2. Is b inside a scope of the function
   Scope is directly dependent on the lexical environment

```js
function a() {
  var b = 10;
  c();
  function c() {
    console.log(b);
  }
}
a();

console.log(b); // It will print not defined
```

suppose we log the b inside c then it will look the local environment any see if b is present if not c will have the reference of the parent and go to the lexical environment of the parent see if there is b and if its not there it will go to the parent of a which here is the global execution context and see whether b is present and if not it will be null or reference error.

**LEXICAL ENVIRONMENT**

Whenever a Execution content is created a lexical environment is also created.
lexical enivironment is the local memory along with the lexical enivironment of its parent.
lexical means inhirerachi or in a sequencetial order

In example we can say c() function is lexicaly sitting inside a() function
It means where it is present physically
Whenever the Execution context is created you also get referrence to the lexical environment of its parent
Lexical environment of Execution context will be Null

Lexcical enviornment is the local memory + reference to the lexical environment of parent

**Scope chain**
The scope chain is how Javascript looks for variables.

### Let & Const

VAR LET CONST
let and const are both used for variable declaration in JavaScript. let is used for variables that can be reassigned, while const is used for constants with values that should not be changed after the initial assignment

1.  let & const declarations are hoisted

VAR, LET, CONST
DEFINE, UPDATE, REDEFINE
const cannot mutate primitive types

VAR

```js
// we can define a var
var number = 100;
console.log(number);

// we can update the var
number = 200;
console.log(number);

// we can redefine a var
var number = 300;
console.log(number);
```

LET

```js
// we can define a let
let amount = 200;
console.log(amount);

// we can update a let
amount = 500;
console.log(amount);

// we cannot redefine let
let amount = 450;
```

CONST

```js
// we can define const
const num = 30;
console.log(num);

// we cannot update const because we cannot assign to an constant variable

num = 45;
console.log(num);

// we cannot redefine const
const num = 20;
```

we can update reference type [array, objects]

```js
const person = { name: "bob" };
person.name = "john";
console.log(person.name);
```

Let & const are allocated memory but in different memory space than Global object
You cannot access these let & const declaration before you have assign a value to it

### Temporal Dead Zone

```js
console.log(ab);
let ab = 10;
```

**TEMPORAL DEAD ZONE**
temporal dead zone is time since the let & const vaiable was hoisted and till initialize some value
whenever you try to access a varibale inside a temporal dead zone it will give you refference error

**REFERENCE ERROR**
The ReferenceError object represents an error when a variable that doesn't exist (or hasn't yet been initialized) in the current scope is referenced.
console.log(x); // ReferenceError: x is not defined

**TYPEERROR**
A type error occurs when you try to perform an operation on a value that is not of the expected data type.
This error typically happens when you try to perform incompatible operations like adding a string and a number or calling a method on an object that doesn't support that method.
var x = "5";
var y = 10;
console.log(x + y); // TypeError: Cannot convert object to primitive value

**SYNTAX ERROR**
A SyntaxError is a type of error that is thrown when there is a typo in the code, creating invalid code - code which cannot be interpreted by the compiler. Some common causes of a SyntaxError are: Missing opening or closing brackets, braces, or parentheses. Missing or invalid semicolons.
if xs == 5 # SyntaxError: invalid syntax

### Block Scope

**Block**
Block is also know as compound statement
A block statement is used to group zero or more statements.
we group multiple statement together in a block so that we can use it where javascript expects one statement

**block scope**
what all variables and functions that are access inside the block
they cannot be accessed outside of that sepcific block

```js
{
  var a = 10;
  let b = 20;
  const c = 30;
  console.log(a);
  console.log(b);
  console.log(c);
  // here within the block we can access the varibale
}
console.log(a);
console.log(b);
console.log(c);
// here we can access only a because var is global scope and let and var are block scope so we can not access outside of the block
```

**Shadowing**
shadowing occurs when a variable declared in a certain scope (e.g. a local variable) has the same name as a variable in an outer scope (e.g. a global variable). When this happens, the outer variable is said to be shadowed by the inner variable.

shadowing occurs when an inner scope declares a variable with the same name as an outer scope.

**VAR**

```js
var a = 100;
{
  var a = 10; // This shadows the above a variable
  console.log(a);
}
console.log(a);
// here if we access the a in the global it will return 10 because it shadow the above a variable
```

**LET**

```js
// But that is not the case in let
let bs = 100;
{
  let bs = 20;
  console.log(bs); // This shadows the above b variable
}
console.log(bs);
// here it will print 100

// For const it works same as let
```

1. Var if it is in the global or block it will be allocated memory in the global object in browser

2. let if it is in the global scope it will allocate the memory in the script object and if it is within block scope then it will be allocated memory in the block object

3. const if it is in the global scope it will allocate the memory in the script object and if it is within block scope then it will be allocated memory in the block object

```js
var d = 100;
function x() {
  var d = 30;
  console.log(d);
}
x();
console.log(d);
// In function also the shadowing works in the same format
```

**ILLEGAL SHADOWING**

```js
let ac = 20;
{
  var ac = 20;
}
// This will throw an syntaxerror : Identifier "a" has already been declared
// You can shadow let using let but you can not shadow let using var
```

```js
var cd = 20;
{
  let cd = 20;
}
// This is a valid shadowing
```

**using function you can shadow**

```js
let ac = 20;
function y() {
  var ac = 20;
}
// This is legal
```

**Block scope also follows lexical scope**

```js
const de = 30;
{
  const de = 100;
  {
    const de = 200;
    console.log(de);
  }
  console.log(de);
}
```

_scope will be same for normal function and arrow function_

<!-- ======================================================================================== -->
