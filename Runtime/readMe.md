# RUNTIME

## AGENDA

- How browser Works underHood
- JS code workflow in browser
- Execution Context
- Call stack
- Event Loop
- callback Queue or [Event Queue]
- Microtask Queue
- Memory Storage(garbage collection)

### What happens behind the scene when you hit URL in the browser?

When you type a website's address into your browser.The browser parses the URL to understand the protocol . The browser checks its local cache to see if it already knows the IP address associated with the domain name. If it is not in cached , the browser sends a DNS (Domain Name System) query to a DNS server to resolve the domain name into an IP address. The browser initiates a TCP connection with the server. And the browser send an HTTP request to the webserver. The server sends out an HTTP response and display HTML content

- It looks for four types of cache
  1. Browser cache
  2. OS cache
  3. router cache
  4. ISP cache

### How javscript code works in browser?

JAVASCRIPT CODE ----> PARSER ----> JS ENGINE

- Javscript code - The code that is written in the Script.js
- Parser - Parser go through line by line and check if the syntax of the code is correct
- JS Engine - Js Engine is computer program that executes javascript code and converts it into computer understandable language (Machine Code)

Firstly the Jscode is parsed and check if the syntax of the code is correct.Now the browser doesn't understand the high level of JS code, so it is send to JS Engine.When the JS Engine scans a script file it makes an environment called Execution Context that handles the entire tranformation and execution of the code.

### What is Execution Context?

When the JS Engine scans a script file it makes an environment called Execution Context that handles the entire tranformation and execution of the code.

There are two types of Execution Context:

- Global Execution Context
- Function Execution Context

Global Execution Context:
The global execution context is created when a JavaScript script first starts to run, and it represents the global scope in JavaScript.

Function Execution Context:
A function execution context is created whenever a function is called, representing the function's local scope.

When a javascript file is created there will be only one Global Execution Context but there could be many Function Execution Context.

### How Execution Context is created?

There will be two components that are memory and code component.

There will be two phases when a Execution Context is created, One is Creation Phase and the other one is Execution Phase

Creation Phase:
During this phase, JavaScript allocates memory for variables and assigns them an initial value of undefined. It also stores functions in memory (hoisting) and sets up the scope chain and this value.

Execution Phase:
In this phase, JavaScript executes the code line by line, performing assignments, computations, and function calls. Functions are executed within their own execution contexts.

As Execution Context has many Function Execution Context and it is managed by Execution Stack.

### What is Call stack?

A Call Stack is a stack with LIFO(Last In First Out) structure, which is used to store all the Execution Context created during the code Execution.

Function Calls: When a function is called in JavaScript, a new execution context for that function is created, which includes information about the function's arguments, local variables, and its scope.

Push onto Stack: This newly created execution context is pushed onto the top of the call stack.

Execution: The function's code is executed within its context. If this function calls other functions, their contexts are also pushed onto the stack, creating a chain of contexts.

Pop from Stack: When a function finishes executing, its context is popped (removed) from the top of the call stack.

Other Names For Call Stack:

- Execution context Stack
- Program Stack
- Control Stack
- Runtime stack
- machine Stack

EXAMPLE:

1. Whenever you call a function for its execution, you are pushing it to the stack.
2. Whenever the execution is completed, the function is popped out of the stack.

```js
function start() {
  next();
}
function next() {
  return "I am next";
}

// Invoke the `start` function
start();
```

1. Add the start() function to the call stack list and execute the code.
2. Add the next() function to the call stack list and execute the code.
3. Delete the next() function from our call stack list.
4. Delete the start() function from the call stack list since there are no items anymore.

### Event Loop

The event loop is a process that continuously monitors both the call stack and the event queue and checks whether or not the call stack is empty. If the call stack is empty and there are pending events in the event queue, the event loop dequeues the event from the event queue and pushes it to the call stack. The call stack executes the event, and any additional events generated during the execution are added to the end of the event queue.

1.  All the callback function which comes through promises will go inside Microtask Queue(more priority)
2.  Other callback function will go inside callback queue

### what is Event Queue?

The event queue follows the queue data structure. It stores async callbacks to be added to the call stack. It is also known as the Callback Queue or Macrotask Queue.

Whenever the call stack receives an async function, it is moved into the Web API. Based on the function, Web API executes it and awaits the result. Once it is finished, it moves the callback into the event queue (the callback of the promise is moved into the microtask queue).

The event queue constantly checks whether or not the call stack is empty. Once the call stack is empty and there is a callback in the event queue, the event queue moves the callback into the call stack. If there is a callback in the microtask queue as well, it is moved first. The microtask queue has a higher priority than the event queue.

### Micro task queue

Micro Task Queue: Micro tasks are higher priority tasks that need to be executed after the currently executing script but before the next macro task. Promises, mutation observers, and queueMicrotask are examples that add jobs to the micro task queue. Micro tasks are executed in a FIFO (First In, First Out) order.

### Memory Storage(garbage collection)

Higher level languages like JS automatically allocates memory when objects are created and free it when they are not used anymore. This is called Garbage Collection.

DATA TYPES:

1. Primitive Types: Stored directly in the "Stack", where it is accessed from.
2. Reference Types: Stored in the heap and accessed by reference.

Primitive types are stored in the stack because they are fixed but reference are not a fixed value in array, object or function so it needs more memory.

### blocking and Non-blocking

- Blocking refers to operations that block further execution until that operation completes
- Non-blocking refers to code that does not block execution

### Javascript Engine

A JavaScript Engine is a software component that Executes javascript code.
It consists of several parts, including the Parser, which parses the code; the Interpreter, which interprets the parsed code; the Compiler, which compiles code for optimization; and the Memory Heap, where objects are allocated memory. Different browsers use their own JavaScript engines, such as V8 in Chrome, SpiderMonkey in Firefox, and JavaScriptCore in Safari.

How it Works

01 Parsing:

- The engine parses the source code to create an Abstract Syntax Tree (AST).

  02 Compilation:

- The engine compiles the code, optimizing it for performance.

  03 Execution:

- The compiled code is executed, and the engine manages the call stack, memory allocation, and other runtime aspects.

  04 Garbage Collection:

- Unused objects are identified and released from memory through garbage collection.

  05 Event Loop:

- In a browser environment, the event loop handles asynchronous tasks, ensuring smooth execution without blocking the main thread.

### Compiling vs Interpreting language

- compiled languages are complied to machine code all at once
- Interpreted languages are interpreted line by line
- compilied languages have a slow write-time and fast run-time and interpreted languages have the opposite

## Working of JS code in browser (optional)

**How JavaScript Code Works in the Browser:**

_Response:_
"When a web page containing JavaScript is loaded in a browser, the browser goes through several steps to interpret and execute the JavaScript code:

1. **HTML Parsing:** The browser parses the HTML markup, creating the Document Object Model (DOM) to represent the structure of the page.

2. **Encounter Script Tag:** When the browser encounters a `<script>` tag (either inline or referencing an external file), it initiates the retrieval and execution of the associated JavaScript code.

3. **JavaScript Engine:** The JavaScript engine in the browser (e.g., V8 in Chrome, SpiderMonkey in Firefox) interprets and executes the JavaScript code. This involves parsing, compiling, and executing the code line by line.

4. **DOM Manipulation:** JavaScript interacts with the DOM, allowing dynamic changes to the content, structure, and styles of the web page. It can add, remove, or modify HTML elements, respond to user interactions, and update the page without requiring a full page reload.

5. **CSSOM Construction:** If there are styles or stylesheets in the page, the browser constructs the CSS Object Model (CSSOM) to represent the styles applied to the DOM.

6. **Render Tree Construction:** The browser combines the DOM and CSSOM to create the Render Tree, a representation of the visual elements on the page.

7. **Layout and Rendering:** The browser performs layout and rendering based on the Render Tree, determining the position and style of each element, and displaying the final visual representation on the user's screen.

8. **Asynchronous Operations:** JavaScript can initiate asynchronous operations such as fetching data from a server (Ajax requests), loading images, or setting timers. These operations are handled by the browser's event loop.

9. **Event Loop:** The event loop continuously checks for events or tasks in the callback queue, executing them in the order they were queued. This ensures that asynchronous operations do not block the main thread.

Understanding this process provides insights into how JavaScript interacts with the browser environment, manipulates the DOM, and contributes to the overall functionality and interactivity of web pages."
