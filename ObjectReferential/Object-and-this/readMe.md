# OBJECTS

# AGENDA

1. OBJECT
   1.1 Creating, modify and deleting an Object
2. FACTORIES AND CONSTRUCTORS
3. This keyword

### OBJECT

An object in JavaScript is a composite data type that allows you to store key-value pairs. It is a collection of properties, where each property has a key and a corresponding value.

How to create an Object
You can create an object using object literal notation, which involves enclosing key-value pairs within curly braces {}

### CREATING OBJECTS

```js
// CREATE
const circle = {
  radius: 1,
  location: {
    x: 1,
    y: 2,
  },
  draw() {
    console.log("draw");
  },
};
circle.draw();

// MODIFY
circle.radius = 2;
console.log(circle);

// DELETE
delete circle.location.x;
console.log(circle);
```

### FACTORIES FUNCTION

A factory function is a function that returns an object. It's called factory function because it creates and returns a new object each time it's called, Just like a factory creates and produces new products.

```js
function createCircle(radius) {
  return {
    radius,
    sqr() {
      console.log("sqr");
    },
  };
}

const sqr = createCircle();
sqr.sqr();
```

### CONSTRUCTOR FUNCTION

constructor is a special function that creates and initialize an object instance of a class.In javascript, a construtor get called when an object is created using the new Keyword.
The purpose of a constructor is to create a new object and set values for any existing object properties

```js
function User(username) {
  this.username = username;
  this.drop = function () {
    console.log(`drop a like for ${this.username}`);
  };
}

const newDrop = new User("harry"); //using new will create a obj{} and this will point to that object and finally it will return the obj
newDrop.drop();

const newPer = new User("gravy");
newPer.drop();
```

### CONSTRUCTOR PROPERTY

If you define let x = {}
javascript turns this into let x = new Object();
every Object has a constructor property

```js
const newfn = new newDrop.constructor("hermoine");
newfn.drop();
```

```js
// call and apply are nothing but a methods for function its a same like new User('harry)
// here it creates a new obj but in call we are explicitly returning the obj and the second arguments

function Persons(username) {
  this.username = username;
  this.drop = function () {
    console.log(`drop a like for ${this.username}`);
  };
}

const objCall = Persons.call({}, "gray");
objCall.drop();
```

If you want to have a private method in the constructor function just do let something = somevalue beacause using this.something can be accessed but using local variable cannot be access outsides

### PRIMITIVES AND REFERENCE TYPES

1.  Primitives are copied by their value
2.  objects are copied by their reference

```js
// PRIMITIVE
let number = 10;
function increase(number) {
  number++;
}
increase(number);
console.log(number); // It will be 10 because primitive are copied by their value and independent

// REFERENCE
let obj = { value: 10 };
function increase(obj) {
  obj.value++;
}
increase(obj);
console.log(obj); // It will be 11 as objects are copied by references
```

### This keyword

This is a keyword that is used to referencing object that is executing the current function.

```js
const objThis = {
  firstName: "patrick",
  lastName: "scott",
  fullName: function () {
    console.log(this);
    console.log(`${this.firstName} ${this.lastName}`);
  },
};
objThis.fullName();
// here this will refer to the current obj

//  Arrow functions do not create their own this binding
// In the arrow function will inherit the scope of the nearest containing regular function
const objThis1 = {
  firstName: "patrick",
  lastName: "scott",
  fullName: () => {
    console.log(this);
    console.log(`${this.firstName} ${this.lastName}`);
  },
};
objThis1.fullName(); // This will not print because this will refer to the global object as arrow function does not allow and it goes not have nearest regular function.

// This will work
const objThis2 = {
  firstName: "patrick",
  lastName: "scott",
  fullName: function () {
    const arrowFunction = () => {
      console.log(this);
      console.log(`${this.firstName} ${this.lastName}`);
    };
    arrowFunction();
  },
};
objThis2.fullName();

// using array
const arrayThis2 = {
  firstName: "patrick",
  lastName: "scott",
  hobbies: ["programming", "music"],
  listHobbies: function () {
    this.hobbies.forEach(function (hobby) {
      console.log(this.firstName);
      console.log(hobby);
    }, this);
  },
};
arrayThis2.listHobbies();
```
