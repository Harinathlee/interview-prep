
# Table of Contents

- [Java Script Basic Concepts](#java-script-basic-concepts)
  - [1. What is JavaScript?](#1-what-is-javascript)
  - [2. JavaScript: The Runtime Environment](#2-javascript-the-runtime-environment)
    - [1. The JS Engine 🚀](#1-the-js-engine-🚀)
    - [2. Web/Global APIs 🌏](#2-webglobal-apis-🌏)
    - [3. Callback Queue (Macrotask Queue) ⌛](#3-callback-queue-macrotask-queue-⌛)
    - [4. Microtask Queue 🔬](#4-microtask-queue-🔬)
    - [5. Event Loop 🔄](#5-event-loop-🔄)
  - [3. What is the difference between let, const, and var?](#3-what-is-the-difference-between-let-const-and-var)
  - [4. What is the difference between “==” and “===”?](#4-what-is-the-difference-between-and-)
  - [5.What are the possible ways to create objects in JavaScript](#5what-are-the-possible-ways-to-create-objects-in-javascript)
  - [6. What is a prototype chain?](#6-what-is-a-prototype-chain)
  - [7. What is NaN Property?](#7-what-is-nan-property)
  - [8. What is the difference between debouncing and throttling, and when would you use each one?](#8-what-is-the-difference-between-debouncing-and-throttling-and-when-would-you-use-each-one)
    - [What is Debouncing?](#what-is-debouncing)
    - [What is Throttling?](#what-is-throttling)
  - [9. What is the difference between the null and the undefined values?](#9-what-is-the-difference-between-the-null-and-the-undefined-values)
  - [10. What is a strict mode in javascript?](#10-what-is-a-strict-mode-in-javascript)
  - [11. What is the difference between cookies, sessionStorage, and localStorage?](#11-what-is-the-difference-between-cookies-sessionstorage-and-localstorage)
  - [12. What are the three types of JavaScript errors?](#12-what-are-the-three-types-of-javascript-errors)
  - [13. What is the use of `this` keyword in JavaScript?](#13-what-is-the-use-of-this-keyword-in-javascript)
  - [14. What are the different data types in JavaScript?](#14-what-are-the-different-data-types-in-javascript)
  - [15. What is Object Destructuring?](#15-what-is-object-destructuring)
  - [16. What is the Temporal Dead Zone](#16-what-is-the-temporal-dead-zone)
  - [17. What is the difference between Call, Apply and Bind](#17-what-is-the-difference-between-call-apply-and-bind)
  - [18. What is the difference between slice and splice in arrays](#18-what-is-the-difference-between-slice-and-splice-in-arrays)
- [Java Script Functions](#java-script-functions)
  - [1. What is Function Declaration/Definition?](#1-what-is-function-declarationdefinition)
  - [2. What is function expression](#2-what-is-function-expression)
  - [3. What is anonymous function?](#3-what-is-anonymous-function)
  - [4. What are First class functions?](#4-what-are-first-class-functions)
  - [5. What is IIFE?](#5-what-is-iife)
  - [6. why let is prefered in for loop js?](#6-why-let-is-prefered-in-for-loop-js)
  - [7. Params vs arguments](#7-params-vs-arguments)
  - [8. What is Callback in JavaScript?](#8-what-is-callback-in-javascript)
  - [9. What is the difference between function and method?](#9-what-is-the-difference-between-function-and-method)
  - [10. What is the use of void(0) in JavaScript?](#10-what-is-the-use-of-void0-in-javascript)
  - [11. What is an arrow function? Give an example.](#11-what-is-an-arrow-function-give-an-example)
  - [12. What are closures?](#12-what-are-closures)
  - [13. What are higher order functions?](#13-what-are-higher-order-functions)
  - [14. What are pure functions?](#14-what-are-pure-functions)
  - [15. What is function currying?](#15-what-is-function-currying)
  - [16. What is memoization](#16-what-is-memoization)
- [Asynchronous Java Script](#asynchronous-java-script)
  - [1. What is a promise](#1-what-is-a-promise)
  - [2. Why do you need a promise](#2-why-do-you-need-a-promise)
  - [3. What are the three states of promise](#3-what-are-the-three-states-of-promise)
  - [4. What are the main rules of promise](#4-what-are-the-main-rules-of-promise)
  - [5. What is promise chaining](#5-what-is-promise-chaining)
  - [6. What is promise.all and promise.allSettled()](#6-what-is-promiseall-and-promiseallsettled)
  - [7. What are events](#7-what-are-events)
  - [8. What is an event flow](#8-what-is-an-event-flow)

# Java Script Basic Concepts

## 1. What is JavaScript?
JavaScript is a Scripting language that enables you to create dynamic web pages. It is often used to create interactivity and animation on web pages, as well as to add functionality to websites.

JavaScript is used in a wide range of web development tasks, including front-end development, back-end development, game development, and mobile app development.
## 2. JavaScript: The Runtime Environment
**Runtime:** 
Runtime is an environment in which a programming/scripting language executes. A runtime system uses data structures like queues, heaps, and stacks to store the variables, function, and manage the memory.

JS runtime environment is a container with all the required things to run JS code. We have 2 types of runtime environments.

- The runtime environment of a Browser (like Google Chrome).
- The Node runtime environment.

Every web browser will have a JS runtime environment. The very main thing here is the JavaScript engine, which is also known as the heart of JS. Without a JS engine, there is no runtime and no JavaScript at all.

A JavaScript Runtime consists of the following components-

- [🚀] The JS Engine.
- [🌏] Web/Global APIs.
- [⌛] Callback Queue.
- [🔬] Microtask Queue.
- [🔄] Event Loop.


![JavaScript Runtime](https://vahid.blog/post/2021-03-21-understanding-the-javascript-runtime-environment-and-dom-nodes/jsRuntimeEnvironment_hufc6622042c18be00aa4535dddfa9305a_166610_1200x1200_fit_q75_lanczos.jpg)

### 1. The JS Engine 🚀:

To write or execute a JS code, we don’t need to install any software because every web browser will have its own JS engine to parse the code for us.( Chrome - v8 js engine).

The main purpose of JS engine is to convert the developer's written JS source code to machine code so that our computer can understand and perform those specific tasks.

**Memory Heap:**
This is a section of unstructured memory that is used for the allocation of objects and variables.

**Call Stack:**
In JavaScript, the call stack is a data structure that keeps track of the order in which functions are called and executed. It operates on a Last-In, First-Out (LIFO) principle, meaning the most recently called function is the first one to finish and be removed from the stack. 

**Here's how it works:**
- When a function is called, a new frame is created and pushed to the top of the call stack. This frame will have information about the function, such as its local variables and arguments.
- The JS engine will start executing the function code.
- If a function is calling another function inside, then a new frame for that function is created and pushed onto the top of the previous one.
- After execution, the function returns a value or gets sent to the web API, and it is popped off the stack. If a function doesn’t return any value, it returns undefined. This is what is meant by the term “JavaScript runs synchronously”; it is single-threaded, so can only do one thing at a time.
- This process will repeat until the stack gets empty.

### 2. Web/Global APIs 🌏
These APIs, provided by the browser or the operating system, allow JavaScript to interact with external resources and perform operations asynchronously. 
Manipulate documents: One of the most common Web APIs used is the DOM API, which allows developers to manipulate HTML and CSS, letting us create, change, and even remove HTML and dynamically apply styles to our web pages.
Draw and manipulate graphics: Widely supported in browsers, the Canvas API and the Web Graphics Library API let us programmatically update pixel data contained in a <canvas> element.
Fetch data from a server: The Fetch API provides an interface for fetching resources across the network by using generic definitions of the Request and Response objects.

### 3. Callback Queue (Macrotask Queue) ⌛

The callback queue stores the callback functions sent from the Web APIs, such as setTimeout, setInterval, XMLHttpRequest, or events like mouse clicks and keyboard inputs. When the call stack is empty and the microtask queue has no priority task, the event loop moves the first task from the callback queue to the call stack for execution.

### 4. Microtask Queue 🔬
Microtask Queue is like the Callback Queue, but Microtask Queue has higher priority asynchronous tasks like promise callbacks and mutation observer callbacks, which are executed as soon as possible, leading to a more responsive user experience. 
For example, in the case of .fetch(), the callback function gets to the microtask Queue.

### 5. Event Loop 🔄
The event loop is a continuous process that constantly checks the call stack, callback queue, and microtask queue. If the call stack is empty, then it looks out for any task present in the micro queue and puts it in the call stack so that it can execute.
If the call stack and micro queue both are empty, then it checks the callback queue and puts it in the call stack if any task is present, scheduling it for execution.


## 3. What is the difference between let, const, and var?
`let` is a type of variable that allows you to declare a variable within a block of code. This means that the variable will be local to the block and will not be shared with any other blocks.

`const` is like a `let` but that can't change its value once it's been set.

`var` allows you to declare a global variable that will be accessible from anywhere in the code.

## 4. What is the difference between “==” and “===”?
`==` is used to check the equality of the variable, and `===` is used to check equality as well as the data types of the variable.

```javascript
   0 == false   // true
   0 === false  // false
   1 == "1"     // true
   1 === "1"    // false
   null == undefined // true
   null === undefined // false
   '0' == false // true
   '0' === false // false
   NaN == NaN or NaN === NaN // false
   []==[] or []===[] //false, refer different objects in memory
   {}=={} or {}==={} //false, refer different objects in memory
//refer different objects in memory , don't check the values.
let a = [1,2]
let b = a
console.log(a === b); // true because b also refers for same array a
```
## 5.What are the possible ways to create objects in JavaScript

 There are many ways to create objects in javascript as mentioned below:

 1. **Object literal syntax:**

    The object literal syntax (or object initializer), is a comma-separated set of name-value pairs wrapped in curly braces.

    ```javascript
    var object = {
         name: "Sudheer",
         age: 34
    };
    ```

    Object literal property values can be of any data type, including array, function, and nested object.

    **Note:** This is one of the easiest ways to create an object.

 2. **Object constructor:**

    The simplest way to create an empty object is using the `Object` constructor. Currently this approach is not recommended.

    ```javascript
    var object = new Object();
    ```

    The `Object()` is a built-in constructor function so "new" keyword is not required. The above code snippet can be re-written as:

    ```javascript
    var object = Object();
    ```

 3. **Object's create method:**

    The `create` method of Object is used to create a new object by passing the specified prototype object and properties as arguments, i.e., this pattern is helpful to create new objects based on existing objects.
    The second argument is optional and it is used to create properties on a newly created object.

    The following code creates a new empty object whose prototype is null.

    ```javascript
    var object = Object.create(null);
    ```
    The following example creates an object along with additional new properties.

    ```javascript
    let vehicle = {
      wheels: '4',
      fuelType: 'Gasoline',
      color: 'Green'
    }
    let carProps = {
      type: {
        value: 'Volkswagen'
      },
      model: {
        value: 'Golf'
      }
    }

    var car = Object.create(vehicle, carProps);
    console.log(car);
    ```

 4. **Function constructor:**

    In this approach, create any function and apply the new operator to create object instances.

    ```javascript
    function Person(name) {
      this.name = name;
      this.age = 21;
    }
    var object = new Person("Sudheer");
    ```

 5. **Function constructor with prototype:**

    This is similar to function constructor but it uses prototype for their properties and methods,

    ```javascript
    function Person() {}
    Person.prototype.name = "Sudheer";
    var object = new Person();
    ```

    This is equivalent to creating an instance with Object.create method with a function prototype and then calling that function with an instance and parameters as arguments.

    ```javascript
    function func() {}

    new func(x, y, z);
    ```

    **(OR)**

    ```javascript
    // Create a new instance using function prototype.
    var newInstance = Object.create(func.prototype)

    // Call the function
    var result = func.call(newInstance, x, y, z),

    // If the result is a non-null object then use it otherwise just use the new instance.
    console.log(result && typeof result === 'object' ? result : newInstance);
    ```
 6. **Object's assign method:**

    The `Object.assign` method is used to copy all the properties from one or more source objects and stores them into a target object.

    The following code creates a new staff object by copying properties of his working company and the car he owns.

    ```javascript
    const orgObject = { company: 'XYZ Corp'};
    const carObject = { name: 'Toyota'};
    const staff = Object.assign({}, orgObject, carObject);
    ```

 7. **ES6 Class syntax:**

    ES6 introduces class feature to create objects.

    ```javascript
    class Person {
      constructor(name) {
        this.name = name;
      }
    }

    var object = new Person("Sudheer");
    ```

 8. **Singleton pattern:**

    A Singleton is an object which can only be instantiated one time. Repeated calls to its constructor return the same instance. This way one can ensure that they don't accidentally create multiple instances.

    ```javascript
    var object = new (function () {
      this.name = "Sudheer";
    })();
    ```
## 6. What is a prototype chain?
A prototype chain in JavaScript is a mechanism that lets objects inherit properties and methods from other objects. It's the foundation for inheritance and property lookup in JavaScript.
The prototype on object instance is available through **Object.getPrototypeOf(object)** or **\_\_proto\_\_** property whereas prototype on constructor function is available through **Object.prototype**.
### How the JavaScript prototype chain works:
```javascript
// Define a human constructor
function Person(name, age) {
    this.name = name;
    this.age = age;
}

// Add a method for greeting
Person.prototype.greet = function() {
    console.log(`Hi, my name is ${this.name} and I'm ${this.age} years old.`);
};

// Create a human instance
const person = new Person('John', 30);

// Access the person's name attribute and output "John"
console.log(person.name);

// Access the greet method of person and output "Hi, my name is John and I'm 30"
person.greet()
 ```
In this example, we create a Person constructor and add a greet method to its prototype object. When we create a person instance using the new keyword, it inherits the greet method from the Person constructor's prototype object.

Because the person object itself does not have a greet method, JavaScript will look up the prototype chain upwards until it finds a matching method.

## 7. What is NaN Property?
The NaN (not a number) property is used to represent a value that does not exist in the number system. The NaN property can be used to check if a number is valid or not.

## 8. What is the difference between debouncing and throttling, and when would you use each one?
### What is Debouncing?
Debouncing waits to execute a function until a certain amount of time has passed since the last time it was called.

This is useful for preventing unnecessary function calls when the user is interacting with an element rapidly, such as when typing in a search bar or scrolling through a list.
```javascript
const debouncingFunction = function (fn, delay) {
  let timeout = null;

  return function () {
    let context = this;
    let args = [...arguments];
    clearTimeout(timeout);
    timeout = setTimeout(function () {
      fn.apply(context, args);
    }, delay);
  };
};
```
### What is Throttling?

Throttling ensures that a function is only executed at most once within a given time period, regardless of how many times it is called.

This is useful for limiting the load on a server or other resource when the user is repeatedly performing an action, such as clicking a button or submitting a form.

For example, if you have a button that submits a form, you could use throttling to prevent the form from being submitted more than once per second.

This would help to protect your server from being overloaded and would also prevent the user from accidentally submitting the form multiple times.

### Here are some specific examples of when to use debouncing and throttling:

**Debouncing:**
- Search bar: Prevent the search results from updating every time the user types a letter.
- Infinite scroll: Prevent the function that loads new content as the user scrolls down the page from being called too often.
- Autocomplete: Prevent autocomplete suggestions from being updated whenever the user types a letter.
  
**Throttling:**
- Button click: Prevent a button from being clicked more than once per second.
- Form submission: Prevent a form from being submitted more than once per minute.
- API calls: Prevent making too many API calls in a short period of time.

## 9. What is the difference between the null and the undefined values?
Variables get assigned a `null` value to indicate they are declared and assigned but don’t point to anything. A `undefined` variable is declared but not initialized.

## 10. What is a strict mode in javascript?
ECMAScript 5 introduced a strict mode that executed the programs and functions strictly. To use strict mode, we write `"use strict";` on the top of our JavaScript file.

## 11. What is the difference between cookies, sessionStorage, and localStorage?
- **Cookies** are small pieces of data stored in a web browser. Use cookies when you need to share data between the client and server, such as for user authentication. 5kb
- **sessionStorage** is designed to store temporary data that is only needed for a single session. Data stored in sessionStorage is lost when the browser window is closed.5MB
- **localStorage** is used to store persistent data that needs to be accessible across sessions even after the browser window or tab is closed and reopened. It provides long-term storage for web applications.  10MB

Below are some of the differences between cookie, local storage and session storage,

| Feature                           | Cookie                             | Local storage    | Session storage     |
| --------------------------------- | ---------------------------------- | ---------------- | ------------------- |
| Accessed on client or server side | Both server-side & client-side. The `set-cookie` HTTP response header is used by server inorder to send it to user.     | client-side only | client-side only    |
| Expiry                          | Manually configured using Expires option | Forever until deleted    | until tab is closed |
| SSL support                       | Supported                          | Not supported    | Not supported       |
| Maximum data size                 | 4KB                                | 5 MB             | 5MB                 |
| Accessible from                            | Any window | Any window | Same tab |
| Sent with requests | Yes | No | No |


## 12. What are the three types of JavaScript errors?
**Syntax Error:** The syntax of the program is not correct.

**Reference Error:** The JavaScript Engine cannot find a reference to a variable or function in memory.

**Type Error:** Trying to reassign a const variable will lead to a Type Error.

## 13. What is the use of `this` keyword in JavaScript?
In JavaScript, the `this` keyword points to the object currently referred. The this keyword is widely used to assign values to object attributes in constructors.

## 14. What are the different data types in JavaScript?
Number, String, Boolean, NULL, Undefined, and Symbol are the seven primitive data types, but the non-primitive data type “object” is also present.

## 15. What is Object Destructuring?
Destructuring is a technique for extracting elements from objects or arrays.
```javascript
const obj = {
	name: 'varun',
	age: 20
};
const arr = [1, 2, 3];
// Destructuring elements from an object
const { name, age } = obj;
// Destructuring elements from an array
const [x, y, z] = arr;
```
## 16. What is the Temporal Dead Zone

The Temporal Dead Zone(TDZ) is a specific period or area of a block where a variable is inaccessible until it has been initialized with a value. This behavior in JavaScript that occurs when declaring a variable with the let and const keywords, but not with var. In ECMAScript 6, accessing a `let` or `const` variable before its declaration (within its scope) causes a ReferenceError. 

Let's see this behavior with an example,

```javascript
function somemethod() {
  console.log(counter1); // undefined
  console.log(counter2); // ReferenceError
  var counter1 = 1;
  let counter2 = 2;
}
```
## 17. What is the difference between Call, Apply and Bind

 The difference between Call, Apply and Bind can be explained with below examples,

 **Call:** The call() method invokes a function with a given `this` value and arguments provided one by one

 ```javascript
 var employee1 = { firstName: "John", lastName: "Rodson" };
 var employee2 = { firstName: "Jimmy", lastName: "Baily" };

 function invite(greeting1, greeting2) {
   console.log(
     greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
   );
 }

 invite.call(employee1, "Hello", "How are you?"); // Hello John Rodson, How are you?
 invite.call(employee2, "Hello", "How are you?"); // Hello Jimmy Baily, How are you?
 ```

 **Apply:** Invokes the function with a given `this` value and allows you to pass in arguments as an array

 ```javascript
 var employee1 = { firstName: "John", lastName: "Rodson" };
 var employee2 = { firstName: "Jimmy", lastName: "Baily" };

 function invite(greeting1, greeting2) {
   console.log(
     greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
   );
 }

 invite.apply(employee1, ["Hello", "How are you?"]); // Hello John Rodson, How are you?
 invite.apply(employee2, ["Hello", "How are you?"]); // Hello Jimmy Baily, How are you?
 ```

 **Bind:** returns a new function, allowing you to pass any number of arguments

 ```javascript
 var employee1 = { firstName: "John", lastName: "Rodson" };
 var employee2 = { firstName: "Jimmy", lastName: "Baily" };

 function invite(greeting1, greeting2) {
   console.log(
     greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
   );
 }

 var inviteEmployee1 = invite.bind(employee1);
 var inviteEmployee2 = invite.bind(employee2);
 inviteEmployee1("Hello", "How are you?"); // Hello John Rodson, How are you?
 inviteEmployee2("Hello", "How are you?"); // Hello Jimmy Baily, How are you?
 ```

 Call and Apply are pretty much interchangeable. Both execute the current function immediately. You need to decide whether it’s easier to send in an array or a comma separated list of arguments. You can remember by treating Call is for **comma** (separated list) and Apply is for **Array**.

 Bind creates a new function that will have `this` set to the first parameter passed to bind().

## 18. What is the difference between slice and splice in arrays

 Some of the major differences in a tabular form:

 | Slice                                        | Splice                                          |
 | -------------------------------------------- | ----------------------------------------------- |
 | Doesn't modify the original array(immutable) | Modifies the original array(mutable)            |
 | Returns the subset of original array         | Returns the deleted elements as array           |
 | Used to pick the elements from array         | Used to insert/delete elements to/from array |

 **Some of the examples of slice() method are:**
 ```javascript                                                 
   let arrayIntegers = [1, 2, 3, 4, 5];
   let arrayIntegers1 = arrayIntegers.slice(0, 2); // returns [1,2]
   let arrayIntegers2 = arrayIntegers.slice(2, 3); // returns [3]
   let arrayIntegers3 = arrayIntegers.slice(4); //returns [5]
   let arrayIntegers4 = arrayIntegers.slice(-3, -1); //returns [3, 4]
   ```
**Some of the examples of splice() method are:**

```javascript
    let arrayIntegersOriginal1 = [1, 2, 3, 4, 5];
    let arrayIntegersOriginal2 = [1, 2, 3, 4, 5];
    let arrayIntegersOriginal3 = [1, 2, 3, 4, 5];

    let arrayIntegers1 = arrayIntegersOriginal1.splice(0, 2); // returns [1, 2]; original array: [3, 4, 5]
    let arrayIntegers2 = arrayIntegersOriginal2.splice(3); // returns [4, 5]; original array: [1, 2, 3]
    let arrayIntegers3 = arrayIntegersOriginal3.splice(3, 1, "a", "b", "c"); 
    //returns [4]; original array: [1, 2, 3, "a", "b", "c", 5]
```

# Java Script Functions
## 1. What is Function Declaration/Definition?
Basic method of creating a function.
```javascript
function sum(a,b){
    return a+b;

}
```
## 2. What is function expression
In JavaScript, a function expression is a way to define a function as a variable.
```javascript
const sum = function(a,b){
    return a+b;
}
```
## 3. What is anonymous function?
Regular function has 2 parts name and a body, But in JavaScript, you can define a function without a name. You can’t use this, super, or new in an anonymous function.

Anonymous functions are functions that don't have a name. it can be accessed by a variable it is stored in.

```javascript
const sum = function(a,b){
    return a+b;
}
const add = (x, y) => x + y;
sum(2,3);
```
Use cases: They are frequently used as callbacks, event handlers, and in higher-order functions.

## 4. What are First class functions?
First class functions are the functions which can be treated like a variable.This allows for powerful patterns like higher-order functions and callbacks.
#### Passed as arguments: 
Functions can be passed as arguments to other functions, enabling powerful patterns like callback functions. 
```javascript
function calculate(x, y, operation) {
     return operation(x, y);
   }
function add(a, b) {
     return a + b;
   }
console.log(calculate(5, 3, add)); // Output: 8
```
#### Returned from functions: 
Functions can be the result of another function, allowing for the creation of higher-order functions.
```javascript
function createMultiplier(factor) {
     return function(x) {
       return x * factor;
     };
   }
const double = createMultiplier(2);
console.log(double(5)); // Output: 10
```
## 5. What is IIFE?
IIFE stands for Immediately Invoked Function Expression. It's a JavaScript design pattern that creates a function expression and immediately executes it.
```javascript
(function(a,b) {
  console.log(a*b);
})(2,3);  //output: 6
```
## 6. why let is prefered in for loop js?
`let` is block scope so it can be accessed within the loop only, `var` is function scoped so it can be accessed outside the loop also which can lead to unwanted bugs.

In a `for` loop, `let` creates a new variable for each iteration, preventing issues with closures. 

With `var`, only one variable is created for the entire loop, potentially leading to unexpected results when referencing the variable in asynchronous callbacks.
```javascript
for (let i = 0; i < 5; i++) {
  setTimeout(() => console.log(i), 1000);
}
// Output: 0 1 2 3 4
for (var i = 0; i < 5; i++) {
  setTimeout(() => console.log(i), 1000);
}
// Output: 5 5 5 5 5 
```
## 7. Params vs arguments
The values which we used in function declaration are called Parameters and the values which we provide while calling function is called arguments.
```javascript
const sum = function(a,b){ // a,b are Parameters
    return a+b;
}
sum(2,3); //2,3 are arguments
```
## 8. What is Callback in JavaScript?
A callback is a JavaScript function passed to another function as an argument, or parameter. This function is executed when the function that it is passed to gets executed.
```javascript
function greet(name, callback) {
  console.log(`Hello, ${name}!`);
  callback();
}
function sayGoodbye() {
  console.log("Goodbye!");
}
greet("John", sayGoodbye);//sayGoodbye is callback function
```

## 9. What is the difference between function and method?
- The major difference between methods and functions in JavaScript is that methods are called on objects while functions are not.
- Method accepts arguments through an object parameter, and function accepts arguments through a parenthesis parameter.
```javascript
let person = {
  name: "Alice",
  greet: function() {
    console.log("Hello, my name is " + this.name);
  }
};

person.greet(); // Output: Hello, my name is Alice
```
### Why do we need callbacks

The callbacks are needed because javascript is an event driven language. That means instead of waiting for a response javascript will keep executing while listening for other events.

### Callback hell:
Callback Hell is a pattern that consists of multiple nested callback functions. It is an anti-pattern because the code is hard to read and modify.

```javascript
async1(function(){
    async2(function(){
        async3(function(){
            async4(function(){
                ....
            });
        });
    });
});
```
## 10. What is the use of void(0) in JavaScript?
`void(0)` is a special keyword in JavaScript that's used to declare a function that doesn't return any value. When you use `void(0)`, it tells the interpreter that this function should not return anything.
```html
<a href="javascript: void(0)">Link</a>
```
When you don't want a link to navigate to another page or reload a page. You can use `javascript: void(0)` to run code that doesn't change the current page.



```javascript
const result = void(1 + 1);
console.log(result);
// undefined
```
`1 + 1` is evaluated but `undefined` is returned. 

## 11. What is an arrow function? Give an example.
Arrow function is a shorter way of writing a function, which makes code easier to read/write.

Arrow functions implicitly bind the this keyword to the enclosing scope, so you don't need to use bind(), call(), or apply() to bind it to the current object.



```javascript
let myFunction = (a, b) => a * b;
console.log(myFunction(5,10) //50
```
For example, arrow functions can help you write code that is easier to read and understand when you need to write several small functions for event listeners.
```javascript
document.getElementById("btn").addEventListener("click", () => {
  document.getElementById("demo").innerHTML += this;
});
```
## 12. What are closures?
A closure is a function that has access to variables in its parent scope(lexical scopin), even after the parent function has finished executing.

#### Lexical Scoping:
JavaScript uses lexical scoping, meaning a variable's scope is determined by its position in the source code. Inner functions have access to variables in their outer functions.


```javascript
function outerFunction() {
  let count = 0;

function innerFunction() { //closure
    count++;
    console.log(count);
  }

  return innerFunction;
}
let counter = outerFunction();
counter(); // Outputs: 1
counter(); // Outputs: 2

```
## 13. What are higher order functions?
Higher order are functions that either accept one or more functions as arguments or returns a function.
```javascript
// Callback function, passed as a parameter in the higher order function
function callbackFunction(){
    console.log('I am  a callback function');
}

// higher order function
function higherOrderFunction(func){
    console.log('I am higher order function')
    func()
}
higherOrderFunction(callbackFunction);  

```
When working with arrays, you can use the `map()`, `reduce()`, `filter()`, and `sort()` functions to manipulate and transform data in an array.

## 14. What are pure functions?
Pure functions are those whose return values only depend on the arguments they receive. We get the same return value if we call a pure function with the same arguments.

## 15. What is function currying?
Function currying is a process in which we convert a function with multiple parameters to a chain of functions with a single parameter.
```javascript
// Normal function
function sum(a, b) {
	return a + b;
}
// Curried function
function currySum(a) {
	return function (b) {
		return a + b;
  }
}
console.log(sum(1, 2));      // 3
console.log(currySum(1)(2))  // 3

```
### 16. What is memoization

Memoization is a functional programming technique which attempts to increase a function’s performance by caching its previously computed results. Each time a memoized function is called, its parameters are used to index the cache. If the data is present, then it can be returned, without executing the entire function. Otherwise the function is executed and then the result is added to the cache.
Let's take an example of adding function with memoization,

```javascript
const memoizAddition = () => {
  let cache = {};
  return (value) => {
    if (value in cache) {
      console.log("Fetching from cache");
      return cache[value]; // Here, cache.value cannot be used as property name starts with the number which is not a valid JavaScript  identifier. Hence, can only be accessed using the square bracket notation.
    } else {
      console.log("Calculating result");
      let result = value + 20;
      cache[value] = result;
      return result;
    }
  };
};
// returned function from memoizAddition
const addition = memoizAddition();
console.log(addition(20)); //output: 40 calculated
console.log(addition(20)); //output: 40 cached
```

# Asynchronous Java Script
## 1. What is a promise

A promise is an object that may produce a single value some time in the future with either a resolved value or a reason that it’s not resolved(for example, network error). It will be in one of the 3 possible states: fulfilled, rejected, or pending.

The syntax of Promise creation looks like below,

```javascript
    const promise = new Promise(function (resolve, reject) {
      // promise description
    });
```
The usage of a promise would be as below,

  ```javascript
    const promise = new Promise(
      (resolve) => {
        setTimeout(() => {
          resolve("I'm a Promise!");
        }, 5000);
      },
      (reject) => {}
    );

    promise.then((value) => console.log(value));
  ```

The action flow of a promise will be as below,

![Screenshot](https://cdn.hashnode.com/res/hashnode/image/upload/v1608296579074/EVhu1y4EF.jpeg?w=1600&h=840&fit=crop&crop=entropy&auto=compress,format&format=webp)


## 2. Why do you need a promise

Promises are used to handle asynchronous operations. They provide an alternative approach for callbacks by reducing the callback hell and writing the cleaner code.

## 3. What are the three states of promise

Promises have three states:

  1. **Pending:** This is an initial state of the Promise before an operation begins
  2. **Fulfilled:** This state indicates that the specified operation was completed.
  3. **Rejected:** This state indicates that the operation did not complete. In this case an error value will be thrown.

## 4. What are the main rules of promise

A promise must follow a specific set of rules:

1. A promise is an object that supplies a standard-compliant `.then()` method
2. A pending promise may transition into either fulfilled or rejected state
3. A fulfilled or rejected promise is settled and it must not transition into any other state.
4. Once a promise is settled, the value must not change.

## 5. What is promise chaining

The process of executing a sequence of asynchronous tasks one after another using promises is known as Promise chaining. Let's take an example of promise chaining for calculating the final result,

```javascript
new Promise(function (resolve, reject) {
  setTimeout(() => resolve(1), 1000);
})
  .then(function (result) {
    console.log(result); // 1
    return result * 2;
  })
  .then(function (result) {
    console.log(result); // 2
    return result * 3;
  })
  .then(function (result) {
    console.log(result); // 6
    return result * 4;
  });
```

In the above handlers, the result is passed to the chain of .then() handlers with the below work flow,

1. The initial promise resolves in 1 second,
2. After that `.then` handler is called by logging the result(1) and then return a promise with the value of result
3. After that the value passed to the next `.then` handler by logging the result(2) and return a promise with result
4. Finally the value passed to the last `.then` handler by logging the result(6) and return a promise with result.

## 6. What is promise.all and promise.allSettled()

**Promise.all** is a promise that takes an array of promises as an input (an iterable), and it gets resolved when all the promises get resolved or any one of them gets rejected. For example, the syntax of promise.all method is below,

```javascript
Promise.all([Promise1, Promise2, Promise3]) .then(result) => {   console.log(result) }) .catch(error => console.log(`Error in promises ${error}`))
```

**Note:** Remember that the order of the promises(output the result) is maintained as per input order.

**Promise.allSettled()**
This method is used when tasks are not dependent on each other, or if you want to know the outcome of all promises, even if some fail. Promise.allSettled() waits for all promises to settle, whether they resolve or reject, and returns an array of objects with the status of each promise. For example, you can use Promise.allSettled() to gather the results of multiple asynchronous operations, regardless of whether they succeeded or failed. 

```javascript
const promise1 = Promise.resolve(3);
const promise2 = new Promise((resolve, reject) => {
  setTimeout(resolve, 2000, 'foo');
});
const promise3 = 42;

Promise.allSettled([promise1, promise2, promise3]).then((results) => {
  results.forEach((result) => {
    console.log(result.status);
    console.log(result.value);
    console.log(result.reason);
  });
});
```
## 7. What are events

Events are "things" that happen to HTML elements. When JavaScript is used in HTML pages, JavaScript can `react` on these events. Some of the examples of HTML events are,

1. Web page has finished loading
2. Input field was changed
3. Button was clicked

Let's describe the behavior of click event for button element,

```javascript
     <!doctype html>
     <html>
      <head>
        <script>
          function greeting() {
            alert('Hello! Good morning');
          }
        </script>
      </head>
      <body>
        <button type="button" onclick="greeting()">Click me</button>
      </body>
     </html>
```
## 8. What is an event flow

Event flow is the order in which event is received on the web page. When you click an element that is nested in various other elements, before your click actually reaches its destination, or target element, it must trigger the click event for each of its parent elements first, starting at the top with the global window object.

There are two ways of event flow
  1. Top to Bottom(Event Capturing)
  2. Bottom to Top (Event Bubbling)


## 9. What is event bubbling

Event bubbling is a type of event propagation where the event first triggers on the innermost target element, and then successively triggers on the ancestors (parents) of the target element in the same nesting hierarchy till it reaches the outermost DOM element(i.e, global window object).

By default, event handlers triggered in event bubbling phase as shown below,

```javascript
    <div>
      <button class="child">Hello</button>
    </div>

    <script>
      const parent = document.querySelector("div");
      const child = document.querySelector(".child");

      parent.addEventListener("click",
        function () {
          console.log("Parent");
        }
      );

      child.addEventListener("click", function () {
        console.log("Child");
      });
    </script>
    // Child
    // Parent
```

## 10. What is event capturing

Event capturing is a type of event propagation where the event is first captured by the outermost element, and then successively triggers on the descendants (children) of the target element in the same nesting hierarchy till it reaches the innermost target DOM element.

You need to pass `true` value for `addEventListener` method to trigger event handlers in event capturing phase.

```javascript
    <div>
      <button class="child">Hello</button>
    </div>

    <script>
      const parent = document.querySelector("div");
      const child = document.querySelector(".child");

      parent.addEventListener("click",
        function () {
          console.log("Parent");
        },
        true
      );

      child.addEventListener("click", function () {
        console.log("Child");
      });
    </script>
    // Parent
    // Child
```
## 11. What is the use of stopPropagation method

The stopPropagation method is used to stop the event from bubbling up the event chain. For example, the below nested divs with stopPropagation method prevents default event propagation when clicking on nested div(Div1)

 ```javascript
 <p>Click DIV1 Element</p>
 <div onclick="secondFunc()">DIV 2
   <div onclick="firstFunc(event)">DIV 1</div>
 </div>

 <script>
 function firstFunc(event) {
   alert("DIV 1");
   event.stopPropagation();
 }

 function secondFunc() {
   alert("DIV 2");
 }
 </script>
 ```
## 12. What is the use of preventDefault method

The preventDefault() method cancels the event if it is cancelable, meaning that the default action or behaviour that belongs to the event will not occur. For example, prevent form submission when clicking on submit button and prevent opening the page URL when clicking on hyperlink are some common use cases.

```javascript
     document
       .getElementById("link")
       .addEventListener("click", function (event) {
         event.preventDefault();
       });
```

**Note:** Remember that not all events are cancelable.

## 13. What is an event delegation

Event delegation is a technique for listening to events where you delegate a parent element as the listener for all of the events that happen inside it.

 For example, if you wanted to detect field changes inside a specific form, you can use event delegation technique,

 ```javascript
 var form = document.querySelector("#registration-form");

 // Listen for changes to fields inside the form
 form.addEventListener(
   "input",
   function (event) {
     // Log the field that was changed
     console.log(event.target);
   },
   false
 );
 ```
## 14. Why is JavaScript treated as Single threaded

JavaScript is a single-threaded language. Because the language specification does not allow the programmer to write code so that the interpreter can run parts of it in parallel in multiple threads or processes. Whereas languages like java, go, C++ can make multi-threaded and multi-process programs.
 
 ## 15. What is the use of setTimeout

The setTimeout() method is used to call a function or evaluate an expression after a specified number of milliseconds. For example, let's log a message after 2 seconds using setTimeout method,

```javascript
      setTimeout(function () {
        console.log("Good morning");
      }, 2000);
```

      **[⬆ Back to Top](#table-of-contents)**

## 16. What is the use of setInterval

The setInterval() method is used to call a function or evaluate an expression at specified intervals (in milliseconds). For example, let's log a message after 2 seconds using setInterval method,

```javascript
      setInterval(function () {
        console.log("Good morning");
      }, 2000);
```

## 17. What is memoization

Memoization is a functional programming technique which attempts to increase a function’s performance by caching its previously computed results. Each time a memoized function is called, its parameters are used to index the cache. If the data is present, then it can be returned, without executing the entire function. Otherwise the function is executed and then the result is added to the cache.
Let's take an example of adding function with memoization,

```javascript
const memoizAddition = () => {
  let cache = {};
  return (value) => {
    if (value in cache) {
      console.log("Fetching from cache");
      return cache[value]; // Here, cache.value cannot be used as property name starts with the number which is not a valid JavaScript  identifier. Hence, can only be accessed using the square bracket notation.
    } else {
      console.log("Calculating result");
      let result = value + 20;
      cache[value] = result;
      return result;
    }
  };
};
// returned function from memoizAddition
const addition = memoizAddition();
console.log(addition(20)); //output: 40 calculated
console.log(addition(20)); //output: 40 cached
```

## 18. What is an async function

An async function is a function declared with the `async` keyword which enables asynchronous, promise-based behavior to be written in a cleaner style by avoiding promise chains. These functions can contain zero or more `await` expressions.

 Let's take a below async function example,

 ```javascript
 async function logger() {
   let data = await fetch("http://someapi.com/users"); // pause until fetch returns
   console.log(data);
 }
 logger();
 ```
