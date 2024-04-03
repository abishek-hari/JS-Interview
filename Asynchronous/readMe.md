### ASYNCHRONOUS

### AGENDA

1. synchronous
2. asynchronous
   2.1 callBack
   2.2 promises
   2.3 Async / Await

## SYNCHRONOUS

synchronous code executes one task at a time, in a sequennce. Each task must wait for the previous one to complete before moving on to the next.

```js
console.log("First");
console.log("Second");
console.log("Third");

// OUTPUT
First;
Second;
Third;
```

Asynchronous code execution allows to execution next instructions immediately without waiting for the previous ones to complete.. It enables non-blocking operations,It means that the program can continue executing code while certain tasks are in progress.

```js
console.log("First");

// Set timeout for 2 seconds
setTimeout(() => console.log("Second"), 2000);

console.log("Third");

// OUTPUT
First;
Third;
Second;
```

Without using callback or promises it return undefined as it executes immediately

```js
const lineup = function (likedBy) {
  setTimeout(() => {
    return `${likedBy}`;
  }, 1000);
};

const msg = lineup("demon");
console.log(msg);
```

The lineup function is asynchronous because it uses setTimeout, which means that it doesn't return a value immediately. Instead, it returns undefined.

Meanwhile, the console.log(message) statement is executed immediately after the lineUp function call. At this point, the arrow function inside setTimeout has not been executed yet, so the value of message is undefined.

### CALLBACKS:

A callback is a function passed as an argument to another function.

```js
const Subscribe = function (name, cb) {
  setTimeout(() => {
    cb(`${name} got SUBSCRIBED!!!`);
  }, 1000);
};

const liked = function (likedBy, cb) {
  setTimeout(() => {
    cb(`${likedBy}`);
  }, 2000);
};

const share = function (shareBy, cb) {
  setTimeout(() => {
    cb(`${shareBy}`);
  }, 3000);
};

Subscribe("gravy", (cb) => {
  console.log(cb);
  liked("demon", (cb) => {
    console.log(cb);
    share("geni", (cb) => {
      console.log(cb);
    });
  });
});
// Callback Hell
```

### PROMISES

Promises are used to handle asynchronous operations in JavaScript
A Promise is an object representing the eventual completion or failure of an asynchronous operation.

PROMISE STATE:
01 - PENDING
02 - FULFILLED
03 - REJECTED

```js
const Subscribe = function (name) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`${name} got SUBSCRIBED!!!`);
      reject("ERROR!!!");
    }, 1000);
  });
};

const liked = function (likedBy) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`${likedBy} got a like!!!`);
      reject("ERROR!!!");
    }, 2000);
  });
};

const share = function (shareBy) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`${shareBy} shared this!!!`);
      reject("ERROR!!!");
    }, 3000);
  });
};

Subscribe("harry")
  .then((res) => {
    console.log(res);
    return liked("hermoine");
  })
  .then((res) => {
    console.log(res);
    return share("gary");
  })
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.log(err);
  });
// promise chaining
// While chaining alway you should return = > THE RETURN KEYWORD IS MUST!!!
```

### ASYNC / AWAIT

**ALWAYS RETURN A PROMISE**

_async/await_ is a feature in JavaScript used to work with asynchronous code. It simplifies the process of dealing with promises and asynchronous operations, making the code more readable and easier to understand.

The async keyword is used to define a function that will return a promise. Within an async function, the await keyword is used to pause the execution of the function until the awaited promise is resolved. This allows writing asynchronous code in a way that looks and behaves more like synchronous code.

```js
const Subscribe = function (name) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`${name} got SUBSCRIBED!!!`);
      reject("ERROR!!!");
    }, 1000);
  });
};

const liked = function (likedBy) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`${likedBy} got a like!!!`);
      reject("ERROR!!!");
    }, 2000);
  });
};

const share = function (shareBy) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(`${shareBy} shared this!!!`);
      reject("ERROR!!!");
    }, 3000);
  });
};

const results = async () => {
  const msg1 = await Subscribe("harry");
  console.log(msg1);
  const msg2 = await liked("hermoine");
  console.log(msg2);
  const msg3 = await share("gravy");
  console.log(msg3);
};
results();
```
