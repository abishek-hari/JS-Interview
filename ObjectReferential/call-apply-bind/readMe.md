### CALL - APPLY - BIND

```js
let name1 = {
  firstname: "antony",
  lastname: "das",
};
let name2 = {
  firstname: "leo",
  lastname: "das",
};
let printFullName = function (loc) {
  console.log(`hello ${this.firstname} ${this.lastname} from ${loc}`);
};

// call - function borrow
// Call: The call() method invokes a function with a given this value and arguments provided one by one
printFullName.call(name1, "Mumbai");
printFullName.call(name2, "karnataka");

// Apply: Invokes the function with a given this value and allows you to pass arguments as an array
printFullName.apply(name1, ["delhi"]); // we passes 2 argument as list

// Bind: returns a new function, allowing you to pass any number of arguments
const printBind = printFullName.bind(name2, "bhutan"); // It will keep copy of the function and then later if we want we can call them
printBind();

// Call and Apply are pretty much interchangeable. Both execute the current function immediately. You need to decide whether it’s easier to send in an array or a comma separated list of arguments. You can remember by treating Call is for comma (separated list) and Apply is for Array.

// Bind creates a new function that will have this set to the first parameter passed to bind().
```
