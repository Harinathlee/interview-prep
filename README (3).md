
# Interview Prep on JS Functions

## 1. What is Function Declaration/Definition
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
## 5.What is IIFE?
IIFE stands for Immediately Invoked Function Expression. It's a JavaScript design pattern that creates a function expression and immediately executes it.
```javascript
(function(a,b) {
  console.log(a*b);
})(2,3);  //output: 6
```
## 6.why let is prefered in for loop js?
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
## 9.What is the difference between function and method?
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
### 13. What are higher order functions?
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



