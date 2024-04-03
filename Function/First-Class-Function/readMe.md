# FIRST-CLASS FUNCTION

What are First Class Function

- Ability to be used like values

_DEFENITION_
**First-Class Functions:** In programming languages, first-class functions refer to a feature where functions are treated as first-class citizens or first-class objects. This means that functions can be assigned to variables, passed as arguments to other functions, returned from functions, and stored in data structures like variables or arrays, just like any other data type

In JavaScript, functions are first-class citizens, which means they are treated as first-class objects. This concept of "first-class functions" is a fundamental aspect of the language and comes with several important characteristics:

1. **Functions as Values**:

   - In JavaScript, functions are treated like any other data type, such as strings, numbers, or objects.
   - You can assign functions to variables, store them in data structures like arrays and objects, and pass them as arguments to other functions.

   ```js
   const greet = function (name) {
     console.log(`Hello, ${name}!`);
   };
   ```

2. **Function Expressions**:

   - You can create anonymous functions (functions without names) and assign them to variables, creating what's known as function expressions.

   ```js
   const add = function (a, b) {
     return a + b;
   };
   ```

3. **Passing Functions as Arguments**:

   - Functions can be passed as arguments to other functions, enabling you to create higher-order functions.
   - This is commonly used for callbacks and event handling.

   ```js
   function performOperation(x, y, operation) {
     return operation(x, y);
   }

   const result = performOperation(5, 3, add);
   ```

4. **Returning Functions from Functions**:

   - Functions can also be returned from other functions, allowing for the creation of closures and factory functions.

   ```js
   function multiplier(factor) {
     return function (x) {
       return x * factor;
     };
   }

   const double = multiplier(2);
   const triple = multiplier(3);
   ```

5. **Storing Functions in Data Structures**:

   - You can store functions in arrays, objects, or other data structures and access them later.

   ```js
   const mathOperations = {
     add: function (a, b) {
       return a + b;
     },
     subtract: function (a, b) {
       return a - b;
     },
   };
   ```

6. **Higher-Order Functions**:

   - Functions that take other functions as arguments or return functions are called higher-order functions. They are powerful for abstraction and code organization.

   ```js
   const numbers = [1, 2, 3, 4, 5];
   const doubled = numbers.map(function (number) {
     return number * 2;
   });
   ```

In summary, first-class functions in JavaScript allow you to work with functions in a flexible and versatile way, treating them as objects that can be assigned, passed, and returned like any other data type. This feature is essential for functional programming paradigms and enables powerful coding techniques like callbacks, closures, and higher-order functions.
