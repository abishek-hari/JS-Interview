# FUNCTION

# AGENDA

1. Function
2. Function Statement
3. Function Declaration
4. Function Expression
5. Anonymous Function
6. Named Function Expression
7. Parameter and Argument
   7.1 Function Definition
   7.2 Function call
8. Arrow Function

**FUNCTION**

A function in JavaScript is a reusable block of code designed to perform a specific task. It is defined using the function keyword, followed by a name, parameters (if any), and a block of code.

```js
// Function Inocation
a();
b();
function a() {
  var x = 10;
  console.log(x);
}

function b() {
  var x = 100;
  console.log(x);
}
```

**Function statement**
A function statement is a way to declare a named function in JavaScript.
It uses the function keyword followed by the function name and a set of parameters.
It gets hoisted to the top of its containing scope during the compilation phase, so it can be called before its declaration in the code.

```js
function add(a, b) {
  return a + b;
}
```

**Function Expression**
When we store a function inside a variable its called function expression.
A function expression is a way to define a function as part of an expression or within another statement.
It can be named (in which case it can refer to itself) or anonymous.
Function expressions are not hoisted like function statements.

```js
// Example (Anonymous Function Expression):
const add = function (a, b) {
  return a + b;
};

// Example (Named Function Expression):
const multiply = function multiply(a, b) {
  return a * b;
};
```

**Function Declaration**
A function declaration is a statement that declares a function in a specific scope.
It uses the function keyword followed by the function name and a set of parameters.
Function declarations are hoisted to the top of their containing scope during compilation, so they can be called before their declaration in the code.

```js
function namedFunction() {
  // Function body
}

// Anonymous function
const anonymousFunction = function () {
  // Function body
};
```

**DIFFERENCE BETWEEN THEM:**

**Hoisting**
Function statements and function declarations are hoisted to the top of their containing scope, so you can call them before their actual declaration in the code.
Function expressions are not hoisted and can only be called after their declaration.

**Usage**
Function declarations and statements are typically used when you want to create named functions that are accessible throughout the entire scope.
Function expressions, especially anonymous ones, are often used for more localized functions or when you need to assign functions to variables or pass them as arguments to other functions.

**Named vs. Anonymous:**

Function statements and function declarations are named by default (they have a name).
Function expressions can be named (like named function expressions) or anonymous (like anonymous function expressions).

**When it loads:**

A function statement loads before any code is executed. This behavior of function statements is called hoisting, which allows a function to be used before it is defined.

A function expression associates a value with a variable, just like any other assignment statement. function expressions load only when the interpreter reaches the definition of the function.

_Function statement and function declarations are same_

**Anonymous**
What is Anonymous function
A function without a name is called anonymous function
function () {

}
It will throw an error

uses
Anonymous function are used in a place where functions are used as value

what is the output of the below code:

```js
var b = function xy() {
  console.log("b called");
};
b();
// If we call b() it will return the value in it
// xy() If we call XY we will get reference error
```

**Parameter and Argument**

_PARAMETER_
A parameter is a variable listed in the function's declaration.
It acts as a placeholder for the value that will be provided when the function is called.
Parameters are defined as part of the function signature and are local variables that can be used within the function's body.

```js
function sub(a, b) {
  return a + b;
}
// Here, 'a' and 'b' are parameters.
```

_ARGUMENT_
An argument is the actual value or expression passed to a function when it's invoked.

```js
const result = sub(5, 3);
// Here, '5' and '3' are arguments passed to the 'add' function.
```

**Function Definition**
A function definition is where you provide the details of how a function should behave. It includes the function's name, parameters, and the code that gets executed when the function is called.

**Function Call**
A function call, also known as invoking or executing a function, is the process of telling a computer to execute the code within a particular function. When you call a function, you are instructing the program to run the set of instructions defined in that function's code block.

```js
// Function Definition
function addNumbers(x, y) {
  return x + y;
}

// Function Call
const result = addNumbers(5, 7);

// Output
console.log(result); // Output: 12
```

**Arrow Function**

Arrow functions in JavaScript provide a more concise syntax for writing functions. They are particularly useful for short and anonymous functions. The key differences from traditional functions include a shorter syntax, a different behavior regarding the this keyword, and the absence of the arguments object

```js
// Traditional Function
function add(x, y) {
  return x + y;
}

// Arrow Function
const addArrow = (x, y) => x + y;

console.log(add(2, 3)); // Output: 5
console.log(addArrow(2, 3)); // Output: 5
```

1. No arguments object in arrow functions
   A normal function has an arguments object which you can access in the function:

```js

function print() {
console.log(arguments)
}
The arguments object is a local variable that contains the arguments passed to the function when called.

print("hello", 400, false)

// {
// '0': 'hello',
// '1': 400,
// '2': false
// }
```

As you can see here, the three arguments passed when calling print() are contained in the arguments object which we log to the console. We can access the first argument with arguments[0], the second with arguments[1] and the third with arguments[2]

But this object does not exist in arrow functions. Let's try it out. Say we have print using an arrow function:

```js
const print = () => {
  console.log(arguments);
};

print("hello", 400, false);
// Uncaught ReferenceError: arguments is not defined
// Now we have a reference error: arguments is not defined. That's because the arguments variable does not exist in arrow functions.
```

2. Arrow functions do not create their own this binding
   In normal functions, a this variable is created which references the objects that call them. For example:

```js
const obj = {
name: 'deeecode',
age: 200,
print: function() {
console.log(this)
}
}

obj.print()
// {
// name: 'deeecode',
// age: 200,
// print: [Function: print]
// }
As you can see here, the this in the print method points to obj, which is the object that calls the method.
```

Here's another example:

```js
const obj = {
  name: "deeecode",
  age: 200,
  print: function () {
    function print2() {
      console.log(this);
    }
    print2();
  },
};

obj.print();
// Window
```

Here, we have two functions. The first one is print which is a method of the obj object. The second is print2 which is a function declared inside print. print2() is also called directly.

In this case, print is called by obj (obj.print()) but no object calls print2 (print2()). So the this in print2 would reference the window object by default.

<!-- IN ARROW FUNCTION -->

Now let's see what happens with an arrow function.

```js
const obj = {
  name: "deeecode",
  age: 200,
  print: () => {
    console.log(this);
  },
};

obj.print();
// Window
```

By using an arrow function for print, this function does not automatically create a this variable. As a result, any reference to this would point to what this was before the function was created.

As you see in the result, this was pointing to the Window object before print was created.

Let's see another example:

```js
const obj = {
  name: "deeecode",
  age: 200,
  print: function () {
    const print2 = () => {
      console.log(this);
    };
    print2();
  },
};

obj.print();
// {
// name: 'deeecode',
// age: 200,
// print: [Function: print]
// }
```

Here, we have print as a normal function which means a this variable is automatically created in it. Then we have print2 which is an arrow function.

Because obj is calling print (as in obj.print()), the this in print would point to obj.

Since print2 is an arrow function, it doesn't create its own this variable. Therefore, any reference to this would point to what the value of this was before the function was created. In this case where obj calls print, this was pointing to obj before print2 was created. As you can see in the results, by logging this from print2, obj is the result.
