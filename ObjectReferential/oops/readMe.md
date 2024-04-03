### OBJECT ORIENTED PROGRAMMING (OOPS)

- A programming paradigm centered around objects rather than function
- It is the programming paradigm that is defined using objects
- Object-Oriented Programming is a programming style based on classes and objects. These group data (properties) and methods (actions) inside a box.
- OOP was developed to make code more flexible and easier to maintain.
- JavaScript is prototype-based procedural language, which means it supports both functional and object-oriented programming.

4 PILLARS
Encapsulation
Abstraction
Inheritance
polymorphism

Before oop we have procedural programming
which divides a program into functions

In **object oriented** programming we combine a group of related variables and functions into a unit. we called the unit as object. we refer these variables as properties and functions as methods.
for example we have localstorage so in that we have property length and methods like setItem and RemoveItem
In oops we group related variable and functions that operator on them into object and this is what we call encapsulation

using Procedural programming

- we have a separate variables and function

```js
let baseSalary = 30000;
let overtime = 10;
let rate = 20;

function getWage(baseSalary, overtime, rate) {
return baseSalary + overtime \* rate;
}
console.log(getWage(baseSalary, overtime, rate));
```

using oops

- we can get the properties directly

```js
let employee = {
base_salary: 20000,
over_time: 20,
rates: 25,
getWages: function () {
return this.base_salary + this.over_time \* this.rates;
},
};
console.log(employee.getWages())
```

### BASICS OF CLASS:

Classes are one of the features introduced in the ES6 version of JavaScript.
A class is a blueprint or template for the object
You can create an object from the class.
The class keyword is used to create classes in javascript.
The constructor() is a method used to initialize the object properties

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  getName() {
    return this.name;
  }
  getAge() {
    return this.age;
  }
}

class House {
  constructor(address, price, residents) {
    this.address = address;
    this.price = price;
    this.residents = residents;
  }

  getAddress = () => {
    return this.address;
  };

  getPrice = () => {
    return this.price;
  };

  getResidents = () => {
    return this.residents;
  };
  addResidents = (resident) => {
    return this.residents.push(resident);
  };
}

const Jhon = new Person("jhon", 21);
const bob = new Person("Bob", 23);
const harry = new Person("harry", 25);

const home = new House("3/135, main street", 25000, [Jhon, bob]);
console.log(home.getResidents());

home.addResidents(harry);
console.log(home.getResidents());
```

### ABSTRACTION

ABSTRACTION
Abstraction is the concept of object-oriented programming that “shows” only essential attributes and “hides” unnecessary information. The main purpose of abstraction is hiding the unnecessary details from the users.
This technique recudes complexity and also isolates the impact of changes in the code

Here we are going to introduce a new method call getHouseDetails
This method abstracts away the internal details of the house, providing a simplified and more high-level representation of the house.

```js
class PersonAbstract {
  constructor(name, age) {
    this.name = name;
    this.age = age;
    this.job = "";
  }

  getName() {
    return this.name;
  }
  getAge() {
    return this.age;
  }
  setJob = (job) => {
    return (this.job = job);
  };
}

class HouseAbstract {
  constructor(address, price, residents) {
    this.address = address;
    this.price = price;
    this.residents = residents;
  }

  getAddress = () => {
    return this.address;
  };

  getPrice = () => {
    return this.price;
  };

  getResidents = () => {
    return this.residents;
  };
  addResidents = (resident) => {
    return this.residents.push(resident);
  };
  getHouseDetails() {
    return `Address: ${this.address}, Price: $${this.price}`;
  }
}

const pedro = new PersonAbstract("pedro", 19);
const house1 = new HouseAbstract("main street", 40000, []);
house1.addResidents(pedro);
pedro.setJob("Developer");
console.log(house1.getResidents());
console.log(house1.getHouseDetails());
```

### ENCAPSULATION

Encapsulation the packing of data and functions into one component or into a single unit, known as a class. It helps in hiding the internal details of an object and preventing direct access to some of its internal components.
Encapsulation in javascript is achieved using closures or using private fields.

```js
class User {
  constructor(name, password) {
    this._name = name;
    let _password = password;
    this.getPassword = () => {
      return _password;
    };
  }
}

const kedar = new User("kedar", 123456);
console.log(kedar.getPassword());
// we can get the password only using the function and cannot access Directly.

class User {
  #name;

  constructor(name, password) {
    this.#name = name;
    this._password = password;
  }

  #printName() {
    console.log(this.#name);
  }

  PrintFromPrivateMethod() {
    this.#printName();
  }
}

const kedar = new User("kedar", 123456);
kedar.PrintFromPrivateMethod();
```

### INHERITANCE

Inheritance makes all properties and methods available to a child class. This allows us to reuse common logic and to model real-world relationships.

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  getName() {
    return this.name;
  }
  getAge() {
    return this.age;
  }
}

class Programmer extends Person {
  constructor(name, age, company, language) {
    super(name, age);
    this.company = company;
    this.language = language;
  }

  sayHi = () => {
    console.log(
      `Hello my name is ${this.()} and I work on ${this.language}`
    );
  };getName
}

const jerry = new Programmer("jerry", 19, "apple", "Javascript");
jerry.sayHi();
```

### POLYMORPHISM

Polymorphism means having different and many forms. We can overwrite a method inherited from a parent class.
Ability to call the same method on different objects and each object responds in different way is called POLYMORPHISM
In real life, for example, a boy at the same time may be a student, a class monitor, etc. So a boy can perform different operations at the same time. This is called polymorphism.

```js
// Base class
class Shape {
  constructor() {}

  // Common method to calculate area
  calculateArea() {
    return "Area calculation not implemented for this shape.";
  }
}

// Derived class 1: Circle
class Circle extends Shape {
  constructor(radius) {
    super();
    this.radius = radius;
  }

  // Override the calculateArea method for circles
  calculateArea() {
    return Math.PI * this.radius ** 2;
  }
}

// Derived class 2: Rectangle
class Rectangle extends Shape {
  constructor(width, height) {
    super();
    this.width = width;
    this.height = height;
  }

  // Override the calculateArea method for rectangles
  calculateArea() {
    return this.width * this.height;
  }
}

// Usage with polymorphism
const shapes = [new Circle(5), new Rectangle(4, 6), new Circle(3)];

for (const shape of shapes) {
  console.log(`Area: ${shape.calculateArea()}`);
}
```

<!-- OOPS QUESTIONS -->

1. Advantages of OOP:

Modularity: OOP divides the code into objects, making it easier to understand, maintain, and debug.
Reusability: Objects can be reused in different parts of the program or in different programs altogether, saving time and effort.
Scalability: OOP allows you to scale your application by adding more objects without affecting the existing code.
Flexibility: OOP allows you to easily modify or extend existing code by adding new objects or modifying existing ones.

2. What are some other programming paradigms other than OOPs?
   Imperative Programming Paradigm
   Declarative Programming Paradigm
   Imperative Programming Paradigm: Imperative programming focuses on HOW to execute program logic and defines control flow as statements that change a program state
   Declarative Programming Paradigm: Declarative programming focuses on WHAT to execute and defines program logic, but not a detailed control flow.

3. A closure is a function that has access to variables in its outer scope, even after the outer function has returned. Closures are used to create private variables and functions in JavaScript.

4. What is the difference between a class and an object?
   A class is a blueprint for creating objects, while an object is an instance of a class.

5. What is a constructor?
   A constructor is a special method in a class that is used to initialize objects of that class. It is called automatically when an object is created.

6. what is Super keyword?
   The super keyword is used to call corresponding methods of a superclass (parent class) from a subclass (child class). It is also used to access the superclass's constructor.

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name); // Calls the superclass's constructor with the provided argument
  }
  speak() {
    super.speak(); // Calls the superclass's speak method
    console.log(`${this.name} barks.`);
  }
}

let dog = new Dog("Buddy");
dog.speak();
// Output:
// Buddy makes a noise.
// Buddy barks.
// In this example, the super keyword is used to call the Animal class's constructor from the Dog class's constructor. It is also used to call the speak method of the Animal class from the speak method of the Dog class.
```

7. what is Static keyword?
   The static keyword is used to define a static method or property for a class. Static methods are called on the class itself, rather than on an instance of the class.

```js
class MyClass {
  static myStaticMethod() {
    return "Hello, static method!";
  }
}

console.log(MyClass.myStaticMethod()); // Output: Hello, static method!
```

8. what is superclass and subclass?
   Superclass (Base Class): A superclass is a class that is extended or inherited by another class. It serves as a template for the subclass, providing common properties and methods that the subclass inherits. The superclass is higher in the inheritance hierarchy.

   Subclass (Derived Class): A subclass is a class that extends or inherits from a superclass. It inherits all the properties and methods of the superclass and can also have its own additional properties and methods. The subclass is lower in the inheritance hierarchy and specializes the behavior of the superclass.

```js
// Superclass
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

// Subclass
class Dog extends Animal {
  constructor(name) {
    super(name); // Call the superclass's constructor
  }
  speak() {
    console.log(`${this.name} barks.`);
  }
}

let dog = new Dog("Buddy");
dog.speak(); // Output: Buddy barks.
```

9. what are exceptions?
   In JavaScript, exceptions are a mechanism for handling runtime errors. When an error occurs during the execution of a program, an exception is thrown, which can be caught and handled by the program to prevent it from crashing.

10. types of inheritance?
    Single inheritance
    Multiple inheritances
    Multi-level inheritance
    Hierarchical inheritance
    Hybrid inheritance
