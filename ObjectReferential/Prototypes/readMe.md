### PROTOTYPE INHERITANCE - every thing in Javascript is Object

Inheritance is one object trying to access another object

Prototypes are hidden objects that are used to share the properties and methods of a parent class with child classes.

Prototype refers to the mechanism by which objects in JavaScript inherit properties and methods from other objects.
Prototype Inheritance is the process where a new object inherits properties and behaviors from its prototype.

Prototype:
In JavaScript, each object has a prototype, which is a reference to another object.
Objects inherit properties and methods from their prototype.
When you attempt to access a property or method on an object, and the object doesn't have it, JavaScript looks for it in the object's prototype, and so on up the prototype chain until it finds the property/method or reaches the end of the chain.

```js
// Creating a prototype object
const animalPrototype = {
  speak: function () {
    console.log("Generic animal sound");
  },
};

// Creating an object that inherits from animalPrototype
const cat = Object.create(animalPrototype);

// Accessing the speak method from the prototype
cat.speak(); // Output: Generic animal sound
```

Prototype Inheritance:
Prototype inheritance refers to the mechanism by which objects inherit properties and behaviors from their prototype.
When you create a new object, it inherits properties and methods from its prototype.

```js
// Creating a prototype object
const animalPrototype = {
  speak: function () {
    console.log("Generic animal sound");
  },
};

// Creating an object that inherits from animalPrototype
const cat = Object.create(animalPrototype);

// Adding a specific method to the cat object
cat.meow = function () {
  console.log("Meow!");
};

// Accessing both the speak and meow methods
cat.speak(); // Output: Generic animal sound
cat.meow(); // Output: Meow!
```

Prototype Chain:
The prototype chain is a series of linked objects where each object has a prototype, and this prototype itself can have a prototype, creating a chain.
When you try to access a property or method on an object, JavaScript looks up the chain until it finds the property/method or reaches the end of the chain.

```js
// Creating a prototype object
const animalPrototype = {
  speak: function () {
    console.log("Generic animal sound");
  },
};

// Creating a more specific prototype that inherits from animalPrototype
const catPrototype = Object.create(animalPrototype);
catPrototype.purr = function () {
  console.log("Purr!");
};

// Creating an object that inherits from catPrototype
const fluffy = Object.create(catPrototype);

// Accessing methods from the prototype chain
fluffy.speak(); // Output: Generic animal sound
fluffy.meow(); // Output: Meow!
fluffy.purr(); // Output: Purr!
```

IMPLEMENTING PROTOTYPES:
We can implement prototypes using three Ways
01 - using Constructor Function
02 - using Class - syntatic sugar
03 - using Object.create()

PROTOTYPE USING CONSTRUCTOR FUNCTION
We can create objects from a function. With the help of a constructor function, built-in objects like arrays, sets, and others are actually implemented.

In JavaScript, a constructor gets called when an object is created using the new keyword. The purpose of a constructor is to create a new object and set its values for any existing object properties.

```js
Factory function - Not an example for prototype just for understanding
function account(name) {
return {
name,
printName() {
console.log(`hello, ${this.name}`);
},
};
}

const harry = account("harry");
harry.printName();
```

Constructor function

```js
function Settings(name) {
  this.name = name;

  this.printName = function () {
    console.log(this.name);
  };
}

const joe = new Settings("joe");
console.log(joe);
joe.printName();
```

“instance” can be used informally to mean an object created using a particular constructor function
With the help of the new keyword we can create an instance of that constructor.

When we create an instance of the constructor object, an empty object is created ({}). This empty object ({}) is then linked to the prototype.

We should never create a function inside of a constructor function. Because every time an instance is created, a new function is created within it which we created inside the constructor function. This will create major issues for performance.

The solution to this problem is prototypes. We can define a function on the prototype of an object directly. So the object created by using that constructor function will have access to that function.

### prototype using Constructor function

```js
function Setting(name) {
this.name = name;
}

Setting.prototype.printName = function () {
console.log(`hello ${this.name}`);
};

const joy = new Setting("joy");
joy.printName();
console.log(Setting.prototype === joy.**proto**);
console.log(Setting.prototype.isPrototypeOf(joy));
```

So now all objects created by this constructor function will have access to the printName() function.

PROTOTYPE USING CLASS

```js
class AccountSetting {
  constructor(name) {
    this.name = name;
  }
  printName() {
    console.log(`Hello ${this.name}`);
  }
}

const dark = new AccountSetting("dark");
dark.printName();
```

Three things to remember about classes
01 - Classes are not hoisted
02 - Classes are first-class citizens
03 - Classes are executed in strict mode.

SETTERS AND GETTERS
These are simple methods of classes which will get and set a value.

```js
class UserCon {
  constructor(name) {
    this._name = name;
  }
  get getName() {
    console.log(this._name);
  }
  set setName(newName) {
    this._name = newName;
  }
}

const kedar = new UserCon("kedar");
kedar.getName;
kedar.setName = "harry poter";
kedar.getName;
```

Static Methods
Static methods are bound to a class and not to the instances of class or object of the class. We can access static methods through classes only and not through the object of that class.

```js
class User {
  constructor(name) {
    this._name = name;
  }

  static anonymous() {
    console.log("anonymous");
  }
}

const kedar = new User("kedar");
kedar.anonymous(); // error
User.anonymous(); // anonymous
```

PROTOTYPES USING OBJECT.CREATE()
The object.create() method returns a new object with the specified prototype object and properties.
The Object.create() static method creates a new object, using an existing object as the prototype of the newly created object.

```js
const UserObj = {
  init(name) {
    this.name = name;
  },
  printName() {
    console.log(`great job ${this.name}`);
  },
};

const alexa = Object.create(UserObj);
alexa.init("wow");
alexa.printName();
```

The newly created object will inherit all the prototype object's properties. You can specify a second parameter to add new properties to the object, that the prototype lacked:

```js
const UserObj1 = {
  printName() {
    console.log(`great work ${this.name}`);
  },
};

let properties = {
  name: {
    value: "jhon",
  },
};

const alex = Object.create(UserObj1, properties);
alex.printName();
```
