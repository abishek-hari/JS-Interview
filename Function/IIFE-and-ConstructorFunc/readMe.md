// Function Declaration
// Function Expression
// Anonymous Function
// First Class Functions
// What is IIFE?
// IIFE - Interview Question
// Closures
// Function Scopes
// Function Scope - Interview Question
// Hoisting in Functions
// Hoisting - Interview Question
// Params vs Arguments
// Spread vs Rest Operators
// Interview Question on params, args, spread, rest
// Callback Function
// Callback Function - Interview Questions
// Arrow Functions
// Arrow function vs Normal Function

// what is IIFE?
// Imdediately invoked function expression

(function (x) {
return (function (y) {
console.log(x);
})(2);
})(1);

// Function scope
var num1 = 20,
num2 = 3,
name = "Dravid";

const multiply = function () {
return num1 \* num2;
};

console.log(multiply());

function getScore() {
var num1 = 2,
num2 = 3;

function add() {
return `${name} scored ${num1 + num2}`;
}
return add();
}

console.log(getScore());

// output based question

// for (var i = 0; i < 5; i++) {
// setTimeout(() => {
// console.log(i);
// }, i \* 1000);
// }

// using var will give you the output of 5 of 5 times because var is not block scope
// using let will give you 0 1 2 3 4

var x = 21;
function hoist() {
console.log(x);
var x = 25;
}
hoist();

// spread vs rest
function getOutput(...one) {
console.log(one[0] \* one[1]);
}
let arr = [2, 3, 4];
getOutput(...arr);

// const fn = (a,...numbers, a, b) => {
// console.log(a, b);
// }
// fn(5,6,7,8) rest parameter must be always last

// Callback function
// a callback function is a function passed into another function as an argument

// Arrow functions vs normal function

// 1. syntax
function square(num) {
return num \* num;
}

const squareArrow = (num) => {
return num \* num;
};

// 2. Implicit 'return' Keyword
const square1 = (num) => num \* num;

// 3. Arguments
function fnArg() {
console.log(arguments);
}
fnArg(1, 2, 3);
// In normal function you can use arguments
// In arrow function you cannot use arguments

// const fnArrowArg = () => {
// console.log(arguments);
// };
// fnArrowArg(1, 2, 3);

// 4. 'this' keyword
let user = {
username: "harry",
code1: () => {
console.log(`greet ${this.username}`); // this refers to the global object
},
code2() {
console.log(`greet ${this.username}`); // this refers to the user object
},
};
user.code1();
user.code2();
