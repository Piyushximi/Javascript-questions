# Javascript-questions

---


### Table of Contents

 


| No. | Questions | No | Questions |
| ----- | ------------------- | ---- | ------------------- |
| 1 | [Scope in javascript](#1) | 22| [let and var keyword](#22) |
| 2 | [Differences between primitives and non-primitives?](#2) | 23| [Destructuring](#23) |
| 3 | [Difference between null and undefined](#3) | 24| [Rest and Spread Operator](#24) |
| 4 | [Difference between == and === operators](#4) | 25 | [object literals](#25) |
| 5 | [Proto and prototype](#5) | 26 | [Template Literals](#26) |
| 6 | [Event Loop / call stack/ event queue](#6) | 27| [Arrow functions / unary function / anonymous function ](#27) |
| 7 | [callback function](#7) | 28 | [Generator-Function / this](#28) |
| 8 | [promise](#8) | 29 | [WINDOW AND DOCUMENT OBJECT](#29) |
| 9 | [Why do you need a promise](#9) | 30 | [cookie, local storage and session storage](#30) |
| 10| [Three states of promise](#10) | 31 | [High order function](#what-is-a-higher-order-function) |
| 11| [promise.all and Promise.allSettled](#11) | | |
| 12| [async function or async/await](#12) | | |
| 13| [Hoisting](#13) | | |
| 14| [closures](#14)| | |
| 15| [Difference between Call, Apply and Bind](#15)| | |
| 16| [Difference between Shallow and Deep copy](#16)| | |
| 17| [Event propagation and bubling and capturing](#17)| | |
| 18| [strict mode in javascript](#18)| | |
| 19| [map, filter reduce, foreach method](#19)| | |
| 20| [attribute and a property](#20)| | |
| 21| [slice,splice, push , pop , shift , unshift methos](#21)| | |

### [coding Exercise](#coding)
### 1
### What is scope in javascript
Scope is the accessibility of variables, functions, and objects in some particular part of your code during runtime. In other words, scope determines the visibility of variables and other resources in areas of your code.
* **Global scope**
    * Variable on function declaration is accessible everywhere through the entire code, including all functions and blocks
* **Local scope**
    * variable declared inside a function or block have local scope They are only accessible with the function or block where they are defined.
* **Block scope**
    * variable let, const declared within a block {} only access with init.


**[⬆ Back to Top](#table-of-contents)**
### 2
### What are the differences between primitives and non-primitives?
**Primitives:** A primitive data type is data that has a primitive value (which has no properties or methods). There are 7 types of primitive data types.

1. string
2. number
3. boolean
4. null
5. undefined
6. bigint
7. symbol

JavaScript language has both primitives and non-primitives but there are few differences between them as below,

| Primitives                 | Non-primitives       |
| -------------------------- | -------------------- |
| These types are predefined | Created by developer |
| These are immutable        | Mutable              |
| Compare by value           | Compare by reference |
| Stored in Stack            | Stored in heap       |
| Contain certain value      | Can contain NULL too |

**[⬆ Back to Top](#table-of-contents)**

### 3
### What is the difference between null and undefined
**Null:** The value null represents the intentional absence of any object value. It is one of JavaScript's primitive values. The type of null value is object.

You can empty the variable by setting the value to null.

```javascript
var user = null;
console.log(typeof user); //object
```
**undefined:** The undefined property indicates that a variable has not been assigned a value, or declared but not initialized at all. The type of undefined value is undefined too.

```javascript
var user; // Value is undefined, type is undefined
console.log(typeof user); //undefined
```
Any variable can be emptied by setting the value to undefined.

```javascript
user = undefined;
```
Below are the main differences between null and undefined,

| Null                                                                                            | Undefined                                                                                               |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| It is an assignment value which indicates that variable points to no object.                    | It is not an assignment value where a variable has been declared but has not yet been assigned a value. |
| Type of null is object                                                                          | Type of undefined is undefined                                                                          |
| The null value is a primitive value that represents the null, empty, or non-existent reference. | The undefined value is a primitive value used when a variable has not been assigned a value.            |
| Indicates the absence of a value for a variable                                                 | Indicates absence of variable itself                                                                    |
| Converted to zero (0) while performing primitive operations                                     | Converted to NaN while performing primitive operations                                                  |

**[⬆ Back to Top](#table-of-contents)**

### 4
### What is the difference between == and === operators
Both are comparison operators. The difference between both the operators is that `“==”` is used to compare values whereas, `“ === “` is used to compare both values and types.

JavaScript provides both strict(===, !==) and type-converting(==, !=) equality comparison. The strict operators take type of variable in consideration, while non-strict operators make type correction/conversion based upon values of variables. The strict operators follow the below conditions for different types,

1. Two strings are strictly equal when they have the same sequence of characters, same length, and same characters in corresponding positions.
2. Two numbers are strictly equal when they are numerically equal. i.e, Having the same number value.
There are two special cases in this,
1. NaN is not equal to anything, including NaN.
2. Positive and negative zeros are equal to one another.
3. Two Boolean operands are strictly equal if both are true or both are false.
4. Two objects are strictly equal if they refer to the same Object.
5. Null and Undefined types are not equal with ===, but equal with ==. i.e,
null===undefined --> false but null==undefined --> true

Some of the example which covers the above cases,

```javascript
0 == false   // true
0 === false  // false
1 == "1"     // true
1 === "1"    // false
null == undefined // true
null === undefined // false
'0' == false // true
'0' === false // false
[]==[] or []===[] //false, refer different objects in memory
{}=={} or {}==={} //false, refer different objects in memory
```

**[⬆ Back to Top](#table-of-contents)**

### 5
### What is a proto and prototype

**Prototype chaining** is used to build new types of objects based on existing ones. It is similar to inheritance in a class based language.

The prototype on object instance is available through **Object.getPrototypeOf(object)** or **\_\_proto\_\_** property whereas prototype on constructors function is available through **Object.prototype**.

**What is the difference between proto and prototype**

The `__proto__` object is the actual object that is used in the lookup chain to resolve methods, etc. Whereas `prototype` is the object that is used to build `__proto__` when you create an object with new.

```javascript
new Employee().__proto__ === Employee.prototype;
new Employee().prototype === undefined;
```
There are few more differences,
| feature    | Prototype                                                    | proto                                                      |
| ---------- | ------------------------------------------------------------ | ---------------------------------------------------------- |
| Access     | All the function constructors have prototype properties.     | All the objects have \_\_proto\_\_ property                |
| Purpose    | Used to reduce memory wastage with a single copy of function | Used in lookup chain to resolve methods, constructors etc. |
| ECMAScript | Introduced in ES6                                            | Introduced in ES5                                          |
| Usage      | Frequently used                                              | Rarely used                                                |

**[⬆ Back to Top](#table-of-contents)**
### 6
### What is an event loop

The event loop is a process that continuously monitors both the call stack and the event queue and checks whether or not the call stack is empty. If the call stack is empty and there are pending events in the event queue, the event loop dequeues the event from the event queue and pushes it to the call stack. The call stack executes the event, and any additional events generated during the execution are added to the end of the event queue.

**Note:** The event loop allows Node.js to perform non-blocking I/O operations, even though JavaScript is single-threaded, by offloading operations to the system kernel whenever possible. Since most modern kernels are multi-threaded, they can handle multiple operations executing in the background.

### What is call stack

Call Stack is a data structure for javascript interpreters to keep track of function calls(creates execution context) in the program. It has two major actions,

1. Whenever you call a function for its execution, you are pushing it to the stack.
2. Whenever the execution is completed, the function is popped out of the stack.

Let's take an example and it's state representation in a diagram format

```javascript
function hungry() {
eatFruits();
}
function eatFruits() {
return "I'm eating fruits";
}

// Invoke the `hungry` function
hungry();
```

The above code processed in a call stack as below,

1. Add the `hungry()` function to the call stack list and execute the code.
2. Add the `eatFruits()` function to the call stack list and execute the code.
3. Delete the `eatFruits()` function from our call stack list.
4. Delete the `hungry()` function from the call stack list since there are no items anymore.

### What is an event queue

The event queue follows the queue data structure. It stores async callbacks to be added to the call stack. It is also known as the Callback Queue or Macrotask Queue.

Whenever the call stack receives an async function, it is moved into the Web API. Based on the function, Web API executes it and awaits the result. Once it is finished, it moves the callback into the event queue (the callback of the promise is moved into the microtask queue).

The event loop constantly checks whether or not the call stack is empty. Once the call stack is empty and there is a callback in the event queue, the event loop moves the callback into the call stack. But if there is a callback in the microtask queue as well, it is moved first. The microtask queue has a higher priority than the event queue.

**[⬆ Back to Top](#table-of-contents)**
### 7
### What is a callback function

A callback function is a function passed into another function as an argument. This function is invoked inside the outer function to complete an action.
Let's take a simple example of how to use callback function

```javascript
function callbackFunction(name) {
console.log("Hello " + name);
}

function outerFunction(callback) {
let name = prompt("Please enter your name.");
callback(name);
}

outerFunction(callbackFunction);
```

**[⬆ Back to Top](#table-of-contents)**

### 8
### What is a promise

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

![Screenshot](https://github.com/sudheerj/javascript-interview-questions/blob/master/images/promises.png)
**[⬆ Back to Top](#table-of-contents)**

### 9
### Why do you need a promise?
Promises are used to handle asynchronous operations. They provide an alternative approach for callbacks by reducing the callback hell and writing the cleaner code.

### 10
### What are the three states of promise

Promises have three states:

1. **Pending:** This is an initial state of the Promise before an operation begins
2. **Fulfilled:** This state indicates that the specified operation was completed.
3. **Rejected:** This state indicates that the operation did not complete. In this case an error value will be thrown.

**[⬆ Back to Top](#table-of-contents)**
### 11
### What is promise.all

Promise.all is a promise that takes an array of promises as an input (an iterable), and it gets resolved when all the promises get resolved or any one of them gets rejected. For example, the syntax of promise.all method is below,

```javascript
Promise.all([Promise1, Promise2, Promise3])
.then(result) => {
   console.log(result)
})
.catch(error => console.log(`Error in promises ${error}`))
```

**Note:** Remember that the order of the promises(output the result) is maintained as per input order.
### Promise.allSettled() 
Promise.allSettled() is typically used when you have multiple asynchronous tasks that are not dependent on one another to complete successfully, or you'd always like to know the result of each promise.
In comparison, the Promise returned by Promise.all() may be more appropriate if the tasks are dependent on each other, or if you'd like to immediately reject upon any of them rejecting.

```javascript
const promises = [fetch('api1'), fetch('api2'), fetch('api3')];

Promise.allSettled(promises)
  .then(results => {
    const successfulResults = [];
    const failedResults = [];

    results.forEach(result => {
      if (result.status === 'fulfilled') {
        successfulResults.push(result.value);
      } else {
        failedResults.push(result.reason);
      }
    });
    
    console.log('Successful API calls:', successfulResults);
    console.log('Failed API calls:', failedResults);
  })
  .catch(error => console.log('Error:', error));
```
**[⬆ Back to Top](#table-of-contents)**
### 12
### What is an async function or async/await

An async function is a function declared with the `async` keyword which enables asynchronous, promise-based behavior to be written in a cleaner style by avoiding promise chains. These functions can contain zero or more `await` expressions.

Let's take a below async function example,

```javascript
async function logger() {
  let data = await fetch("http://someapi.com/users"); // pause until fetch returns
  console.log(data);
}
logger();
```
### async/await
Async await is a way to handle the promises

when you have a function that return a promise you can handle the promise with `.then(()=>{})` and `.catch(()=>{})` and if you tell this is async operation put await in front of the function invocation and the invocation itself has to be inside a function that’s marked as async.

An async function is a function declared with the async keyword, and the await keyword is permitted within them. The async and await keywords enable asynchronous, promise-based behaviour
- async and await make promises easier to write"
- async makes a function return a Promise
- await makes a function wait for a Promise

It is basically syntax sugar over ES2015 promises and generators.
**[⬆ Back to Top](#table-of-contents)**

### 13
### What is Hoisting

Hoisting is a JavaScript mechanism where variables, function declarations and classes are moved to the top of their scope before code execution. Remember that JavaScript only hoists declarations, not initialisation.
Let's take a simple example of variable hoisting,

```javascript
console.log(message); //output : undefined
var message = "The variable Has been hoisted";
```

The above code looks like as below to the interpreter,

```javascript
var message;
console.log(message);
message = "The variable Has been hoisted";
```

In the same fashion, function declarations are hoisted too

```javascript
message("Good morning"); //Good morning

function message(name) {
console.log(name);
}
```

This hoisting makes functions to be safely used in code before they are declared.

**[⬆ Back to Top](#table-of-contents)**
### 14
 ### What are closures

A closure is the combination of a function and the lexical environment within which that function was declared. i.e, It is an inner function that has access to the outer or enclosing function’s variables. The closure has three scope chains

1. Own scope where variables defined between its curly brackets
2. Outer function’s variables
3. Global variables

Let's take an example of closure concept,

```javascript
function Welcome(name) {
   var greetingInfo = function (message) {
      console.log(message + " " + name);
   };
   return greetingInfo;
}
var myFunction = Welcome("John");
myFunction("Welcome "); //Output: Welcome John
myFunction("Hello Mr."); //output: Hello Mr.John
```

As per the above code, the inner function(i.e, greetingInfo) has access to the variables in the outer function scope(i.e, Welcome) even after the outer function has returned.

**[⬆ Back to Top](#table-of-contents)**

### 15
### What is the difference between Call, Apply and Bind

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

**bind:** returns a new function, allowing you to pass any number of arguments

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

Call and apply are pretty interchangeable. Both execute the current function immediately. You need to decide whether it’s easier to send in an array or a comma separated list of arguments. You can remember by treating Call is for **comma** (separated list) and Apply is for **Array**.

Whereas Bind creates a new function that will have `this` set to the first parameter passed to bind().

**[⬆ Back to Top](#table-of-contents)**

### 16
### What is the difference between Shallow and Deep copy

There are two ways to copy an object,

**Shallow Copy:**
Shallow copy is a bitwise copy of an object. A new object is created that has an exact copy of the values in the original object. If any of the fields of the object are references to other objects, just the reference addresses are copied i.e., only the memory address is copied.

**Example**

```javascript
var empDetails = {
 name: "John",
 age: 25,
 expertise: "Software Developer",
};
```

to create a duplicate

```javascript
var empDetailsShallowCopy = empDetails; //Shallow copying!
```

if we change some property value in the duplicate one like this:

```javascript
empDetailsShallowCopy.name = "Johnson";
```

The above statement will also change the name of `empDetails`, since we have a shallow copy. That means we're losing the original data as well.

**Deep copy:**
A deep copy copies all fields, and makes copies of dynamically allocated memory pointed to by the fields. A deep copy occurs when an object is copied along with the objects to which it refers.

**Example**

```javascript
var empDetails = {
 name: "John",
 age: 25,
 expertise: "Software Developer",
};
```

Create a deep copy by using the properties from the original object into new variable

```javascript
var empDetailsDeepCopy = {
 name: empDetails.name,
 age: empDetails.age,
 expertise: empDetails.expertise,
};
```

Now if you change `empDetailsDeepCopy.name`, it will only affect `empDetailsDeepCopy` & not `empDetails`

**[⬆ Back to Top](#table-of-contents)**

### 17
### What is an event propagation

Event propagation is a mechanism that defines how an event propagates or travels through the DOM tree to arrive at its target and what happens to it afterward.
There are two possible ways in which an event can be propagated —

1. Top to Bottom(Event Capturing)
2. Bottom to Top (Event Bubbling)

### What is event bubbling

Event bubbling is a type of event propagation where the event first triggers on the innermost target element, and then successively triggers on the ancestors (parents) of the target element in the same nesting hierarchy till it reaches the outermost DOM element.
```javascript
// When the event is propagated from the target element to the root element, it is known as bubbling
//Example: We have three divs — child, parent and grandparent.
// The order of execution of the event handlers will be when we click on child
// child > parent > grandparent. This is known as bubbling up of the event.
document.querySelector('#grandparent').addEventListener('click', () => {
   print('Grandparent click event')
})
```

### What is event capturing

Event capturing is a type of event propagation where the event is first captured by the outermost element, and then successively triggers on the descendants (children) of the target element in the same nesting hierarchy till it reaches the innermost DOM element.
```javascript
//when it is propagated from the root element to the target element, it is known as capturing.
//Example: We have three divs — child, parent and grandparent.
// The order of execution of the event handlers will be when we click on child First,
// the grandparent listener will be triggered, then the parent, and finally the child.
// This is also known as trickling down of the event
document.querySelector('#grandparent').addEventListener('click', () => {
   print('Grandparent click event')
}, true)
```


**[⬆ Back to Top](#table-of-contents)**

### 18
### What is a strict mode in javascript
The JavaScript provides "use strict"; expression to enable the strict mode.Strict mode is useful to write "secure" JavaScript by notifying "bad syntax" into real errors. For example, it eliminates accidentally creating a global variable by throwing an error and also throws an error for assignment to a non-writable property, a getter-only property, a non-existing property, a non-existing variable, or a non-existing object.
### How do you declare strict mode
The strict mode is declared by adding "use strict"; to the beginning of a script or a function.
If declared at the beginning of a script, it has global scope.

```javascript
"use strict";
x = 3.14; // This will cause an error because x is not declared
```

and if you declare inside a function, it has local scope

```javascript
x = 3.14; // This will not cause an error.
myFunction();

function myFunction() {
"use strict";
y = 3.14; // This will cause an error
}
```

**[⬆ Back to Top](#table-of-contents)**


### 19
### map, filter reduce, foreach method

**map():** if you want to transform any array with the help of map function we can transform it
```javascript
const numbers = [1, 2, 3, 4];
const doubled = numbers.map(item => item * 2);
console.log(doubled); // [2, 4, 6, 8] 
```
**filter():** filter is used when we want to filter the array to obtain required value. It creates a new array by removing elements that don’t belong and get pushed to the output array.
```javascript
const numbers = [1, 2, 3, 4];
const evens = numbers.filter(item => item % 2 === 0);
console.log(evens); // [2, 4]
```
**reduce():**  is a higher order function used in data manipulation that is used to reduce the array to a single value. Its passes two arguments one function(which includes accumulator and current value) and another initial value
```javascript
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce(function (accumulator , current ) {
 return accumulator + current ;
}, 0);
console.log(sum); // 10
```
* **Accumulator:** This contains the value calculated from the previous iteration. On the first iteration, if an initialValue will be provided, the accumulator will be set to the value of initialValue.
* **CurrentValue:** The current value of the element is processed in the array.
* **CurrentIndex:** The index of the current element is processed in the array.
* **Array:** The original array on which the reduce() method was called.

**Difference map forEach Filter Return Value**
* map() will return a new array as per the conditions applied.
* forEach() will not return anything. forEach() returns undefined.
* filter()method will return an array of matching elements else will return an empty array if no matching happens.

**[⬆ Back to Top](#table-of-contents)**

### 20
### What is the difference between an attribute and a property

Attributes are defined on the HTML markup whereas properties are defined on the DOM. For example, the below HTML element has 2 attributes type and value,

```javascript
<input type="text" value="Name:">
```

You can retrieve the attribute value as below,

```javascript
const input = document.querySelector("input");
console.log(input.getAttribute("value")); // Good morning
console.log(input.value); // Good morning
```

And after you change the value of the text field to "Good evening", it becomes like

```javascript
console.log(input.getAttribute("value")); // Good evening
console.log(input.value); // Good evening
```

**[⬆ Back to Top](#table-of-contents)**

### 21
### slice
Slice method returns selected element in an array, as a new array slice method does not change the original array:

`Let a = [1,2,3,4,5]    let b = a.slice(0,2)  === [1,2]`
### splice
splice used to add/remove item from an array. This method change the original array. `Splice(start, deleteCount, replaceValue)`
```javascript
Var arr = [1,2,3,4,5,6,7]
Var arr1 = [“Piyush”, “Sid”, “Abhi”]
arr.splice(2,1);
//console.log(arr) === [1,2,4,5,6,7] it remove the element of index 2
arr1.splice(2,0, “test”)
//console.log(arr1) === [ 'Piyush', 'Sid', 'test', 'Abhi' ]
```

### push
add new item to the end of array

```javascript
const fruits = ["Banana", "Apple"];
fruits.push(“Mango”);
console.log(fruits)
["Banana", "Apple", "Mango"]
```
### pop
remove the last item of an array
```javascript
const fruits = ["Banana", "Apple", "Mango"];
fruits.pop(“Mango”);
console.log(fruits)
["Banana", "Apple"]
```
### shift
Remove the first item of an array
```javascript
const fruits = ["Banana", "Apple", "Mango"];
fruits.shift()
console.log(fruits)
[ "Apple”, “Mango”]
```
### unshift 
Add new item at the begginning of the array.
```javascript
const fruits = [ "Apple", "Mango"];
fruits.unshift(“Banana”) onsole.log(fruits)
["Banana", "Apple", "Mango"]
```

**[⬆ Back to Top](#table-of-contents)**
### 22
### What is the purpose of the let keyword

The `let` statement declares a **block scope local variable**. Hence the variables defined with let keyword are limited in scope to the block, statement, or expression on which it is used. Whereas variables declared with the `var` keyword used to define a variable globally, or locally to an entire function regardless of block scope.

Let's take an example to demonstrate the usage,

```javascript
let counter = 30;
if (counter === 30) {
let counter = 31;
console.log(counter); // 31
}
console.log(counter); // 30 (because the variable in if block won't exist here)
```

### What is the difference between let and var

You can list out the differences in a tabular format

| var                                                   | let                         |
| ----------------------------------------------------- | --------------------------- |
| It is been available from the beginning of JavaScript | Introduced as part of ES6   |
| It has function scope                                 | It has block scope          |
| Variables will be hoisted                             | Hoisted but not initialized |

Let's take an example to see the difference,

```javascript
function userDetails(username) {
if (username) {
console.log(salary); // undefined due to hoisting
console.log(age); // ReferenceError: Cannot access 'age' before initialization
let age = 30;
var salary = 10000;
}
console.log(salary); //10000 (accessible due to function scope)
console.log(age); //error: age is not defined(due to block scope)
}
userDetails("John");
```

**[⬆ Back to Top](#table-of-contents)**

### 23
### Destructuring
Destructuring is a JavaScript expression that allows us to extract data from arrays and objects and set them into new, distinct variables. Destructuring allows us to extract multiple properties, or items, from an array at a time

```javascript
Object Destructing
const person = {
 firstName: "Piyush",
 lastName: "Sharma",
}
const { firstName, lastName } = person;
console.log(firstName) // Piyush

Array Destructing
let greeting =['Good','Morning'];  
let [g1, g2] = greeting;  
console.log (g1, g2); // Good Morning
```

**[⬆ Back to Top](#table-of-contents)**
### 24
### What is a rest parameter
Javascript uses three dots `(...)` for both the rest and spread operations. But these two operators are not the same

The rest operator is used to collect all the remaining element into array. The rest operator was needed because when function with multiple argument it help to handle it. Rest operator passed in the end of argument if we passed in the starting it will throw error.
```javascript
function myBio(firstName, lastName, ...otherInfo) {
 return otherInfo;
}
myBio(“piyush”, "Sharma”, “Haryana”, "Web Developer", "Male");
[ 'Haryana', 'Web Developer', 'Male' ]
```
For example, let's take a sum example to calculate on dynamic number of parameters,
```javascript
function sum(...args) {
 let total = 0;
 for (const i of args) {
   total += i;
 }
 return total;
}

console.log(sum(1, 2)); //3
console.log(sum(1, 2, 3)); //6
console.log(sum(1, 2, 3, 4)); //13
console.log(sum(1, 2, 3, 4, 5)); //15
```

### What is a spread operator

The Spread operator helps us to copy and expand an expression where multiple argument are needed. It allows us the privilege to obtain a list of parameters from an array.

```javascript
function calculateSum(x, y, z) {
 return x + y + z;
}
const numbers = [1, 2, 3];
console.log(calculateSum(...numbers)); // 6
//Second
const value = [1,2,3]
const newValue = [...value, 4,5,6];
console.log(newValue) //[ 1, 2, 3, 4, 5, 6 ]
```
**[⬆ Back to Top](#table-of-contents)**

### 25
### What are enhanced object literals

Object literals make it easy to quickly create objects with properties inside the curly braces. For example, it provides shorter syntax for common object property definition as below.

```javascript
//ES6
var x = 10,
 y = 20;
obj = { x, y };
console.log(obj); // {x: 10, y:20}
//ES5
var x = 10,
 y = 20;
obj = { x: x, y: y };
console.log(obj); // {x: 10, y:20}
```

**[⬆ Back to Top](#table-of-contents)**

### 26
### What are template literals

Template literals or template strings are string literals allowing embedded expressions. These are enclosed by the back-tick (`) character instead of double or single quotes.
In ES6, this feature enables using dynamic expressions as below,

```javascript
var greeting = `Welcome to JS World, Mr. ${firstName} ${lastName}.`;
```

In ES5, you need break string like below,

```javascript
var greeting = 'Welcome to JS World, Mr. ' + firstName + ' ' + lastName.`
```

**Note:** You can use multi-line strings and string interpolation features with template literals.

**[⬆ Back to Top](#table-of-contents)**

### 27
### What are lambda or arrow functions

An arrow function is a shorter syntax for a function expression and does not have its own **this, arguments, super, or new.target**. These functions are best suited for non-method functions, and they cannot be used as constructors.
* Arrow functions reduce the size of the code.
* The return statement and function brackets are optional for single-line functions.
* It increases the readability of the code.
* Arrow functions provide a lexical this binding. It means, they inherit the value of `this` from the enclosing scope. This feature can be advantageous when dealing with event listeners or callback functions where the value of `this` can be uncertain.

**Limitations of Arrow Functions**
* Arrow functions do not have the prototype property.
* Arrow functions cannot be used with the new keyword.
* Arrow functions cannot be used as constructors.
* These functions are anonymous and it is hard to debug the code.
* Arrow functions cannot be used as generator functions that use the yield keyword to return multiple values over time.


### What is a unary function?

Unary function (i.e. monadic) is a function that accepts exactly one argument. It stands for single argument accepted by a function.

```js
// Unary function
const unaryFunction = (number) => number + 10;

console.log(unaryFunction(10)); // 20
```
    
### What is an anonymous function?

An anonymous function is a function without a name. Anonymous functions are commonly assigned to a variable name or used as a callback function.

**Example 01:** Anonymous function

```js
let show = function () {
  console.log("Anonymous function");
};
show();
```

**Example 02:** anonymous functions as arguments

```js
setTimeout(function () {
  console.log("Execute later after 1 second");
}, 1000);
```

**Example 03:** Immediately invoked function execution

```js
const person = {
  firstName: "Ayaan",
  lastName: "Memon"
};

(function () {
  console.log(person.firstName + " " + person.lastName); // Ayaan Memon
})(person);
```

**Example 04:** Arrow functions

```js
let add = (a, b) => a + b;

add(10, 20); // 30
```

**[⬆ Back to Top](#table-of-contents)**

### 28 
### Explain how `this` works in JavaScript?

The `this` keyword refers to an `object`. Which object depends on how this is being invoked (used or called). The `this` keyword refers to different objects depending on how it is used.

* In an object method, `this` refers to the object.
* Alone, `this` refers to the global object.
* In a function, `this` refers to the global object.
* In a function, in strict mode, `this` is `undefined`.
* In an event, `this` refers to the element that received the event.
* Methods like `call()`, `apply()`, and `bind()` can refer `this` to any object.

**Example:**

```js
// this keyword in object method

const person = {
  firstName: "Nirupama",
  lastName: "Randhawa",
  getName: function () {
    return this.firstName + " " + this.lastName;
  }
};
```

### What is generator in JS?

**Generator-Function:**

A generator-function is defined like a normal function, but whenever it needs to generate a value, it does so with the `yield` keyword rather than `return`. The `yield` statement suspends function\'s execution and sends a value back to caller, but retains enough state to enable function to resume where it is left off. When resumed, the function continues execution immediately after the last `yield` run.

**Syntax:**

```js
function* gen() {
     yeild 1;
     yeild 2;
     ...
     ...
}
```

**Generator-Object:**

Generator functions return a generator object. Generator objects are used either by calling the next method on the generator object or using the generator object in a "for in" loop.

**Example:**

```js
// Generate Function

function* fun() {
  yield 10;
  yield 20;
  yield 30;
}

// Calling the Generate Function
var gen = fun();
gen.next().value; // 10
gen.next().value; // 20
gen.next().value; // 30
```


**[⬆ Back to Top](#table-of-contents)**

### 29
### What is the difference between window and document object?

**1. Window Object**: 

The window object is the topmost object of the DOM hierarchy. It represents a browser window or frame that displays the contents of the webpage. Whenever a window appears on the screen to display the contents of the document, the window object is created.

**Syntax:**

```js
window.property_name;
```

**Window Object Properties:**

|Property	        |Description                            |
|-----------------|---------------------------------------|
|closed	          |Returns a boolean true if a window is closed.|
|console	        |Returns the Console Object for the window.|
|document	        |Returns the Document object for the window.|
|frames	          |Returns all window objects running in the window.|
|history	        |Returns the History object for the window.|
|innerHeight	    |Returns the height of the window's content area (viewport) including scrollbars|
|innerWidth	      |Returns the width of a window's content area (viewport) including scrollbars|
|localStorage	    |Allows to save key/value pairs in a web browser. Stores the data with no expiration date|
|location	        |Returns the Location object for the window.|
|navigator	      |Returns the Navigator object for the window.|
|opener	          |Returns a reference to the window that created the window|
|outerHeight	    |Returns the height of the browser window, including toolbars/scrollbars|
|outerWidth     	|Returns the width of the browser window, including toolbars/scrollbars|
|pageXOffset	    |Returns the pixels the current document has been scrolled (horizontally) from the upper left corner of the window|
|pageYOffset	    |Returns the pixels the current document has been scrolled (vertically) from the upper left corner of the window|
|parent	          |Returns the parent window of the current window|
|screen	          |Returns the Screen object for the window|
|screenLeft	      |Returns the horizontal coordinate of the window relative to the screen|
|screenTop	      |Returns the vertical coordinate of the window relative to the screen|
|screenX	        |Returns the horizontal coordinate of the window relative to the screen|
|screenY	        |Returns the vertical coordinate of the window relative to the screen|
|sessionStorage	  |Allows to save key/value pairs in a web browser. Stores the data for one session|
|scrollX	        |An alias of pageXOffset|
|scrollY	        |An alias of pageYOffset|
|self	            |Returns the current window|
|top	            |Returns the topmost browser window|

**2. Document Object:** 

The document object represent a web page that is loaded in the browser. By accessing the document object, we can access the element in the HTML page. The document object can be accessed with a `window.document` or just `document`.

**Syntax:**

```js
document.property_name;
```

**Document Object Properties:**

|Property       	    |Description                         |
|---------------------|------------------------------------|
|addEventListener()	  |Attaches an event handler to the document|
|baseURI	            |Returns the absolute base URI of a document|
|body	                |Sets or returns the document's body (the `<body>` element)|
|characterSet	        |Returns the character encoding for the document|
|close()	            |Closes the output stream previously opened with document.open()|
|cookie	              |Returns all name/value pairs of cookies in the document|
|createAttribute()	  |Creates an attribute node|
|createElement()	    |Creates an Element node|
|createEvent()	      |Creates a new event|
|createTextNode()	    |Creates a Text node|
|defaultView	        |Returns the window object associated with a document, or null if none is available.|
|designMode	          |Controls whether the entire document should be editable or not.|
|doctype            	|Returns the Document Type Declaration associated with the document|
|documentElement	    |Returns the Document Element of the document (the <html> element)|
|documentURI	        |Sets or returns the location of the document|
|forms	              |Returns a collection of all `<form>` elements in the document|
|getElementById()	    |Returns the element that has the ID attribute with the specified value|
|getElementsByClassName()|	Returns an HTMLCollection containing all elements with the specified class name|
|getElementsByName()	|Returns an live NodeList containing all elements with the specified name|
|getElementsByTagName()|	Returns an HTMLCollection containing all elements with the specified tag name|
|images	              |Returns a collection of all `<img>` elements in the document|
|normalize()	        |Removes empty Text nodes, and joins adjacent nodes|
|open()	              |Opens an HTML output stream to collect output from document.write()|
|querySelector()	    |Returns the first element that matches a specified CSS selector(s) in the document|
|querySelectorAll()	  |Returns a static NodeList containing all elements that matches a specified CSS selector(s) in the document|
|readyState	          |Returns the (loading) status of the document|
|referrer	            |Returns the URL of the document that loaded the current document|
|removeEventListener()|Removes an event handler from the document (that has been attached with the addEventListener() method)|
|title	              |Sets or returns the title of the document|
|URL	                |Returns the full URL of the HTML document|
|write()	            |Writes HTML expressions or JavaScript code to a document|
|writeln()	          |Same as write(), but adds a newline character after each statement|

**Difference:**

| Window | Document |
|------- | ---------|
| It is the root level element in any web page  | It is the direct child of the window object. This is also known as Document Object Model(DOM) |
| By default window object is available implicitly in the page | You can access it via window.document or document.  |
| It has methods like alert(), confirm() and properties like document, location | It provides methods like getElementById(), getElementByTagName(), createElement() etc  |

**[⬆ Back to Top](#table-of-contents)**

### 30
### What are the differences between cookie, local storage and session storage

Below are some of the differences between cookie, local storage and session storage,

| Feature                           | Cookie                             | Local storage    | Session storage     |
| --------------------------------- | ---------------------------------- | ---------------- | ------------------- |
| Accessed on client or server side | Both server-side & client-side     | client-side only | client-side only    |
| Lifetime                          | As configured using Expires option | until deleted    | until tab is closed |
| SSL support                       | Supported                          | Not supported    | Not supported       |
| Maximum data size                 | 4KB                                | 5 MB             | 5MB                 |

**[⬆ Back to Top](#table-of-contents)**


### What is a Cookie
A cookie is a piece of data that is stored on your computer to be accessed by your browser. Cookies are saved as key/value pairs.
For example, you can create a cookie named username as below,

```javascript
document.cookie = "username=John";
```
    
### What is the main difference between localStorage and sessionStorage

LocalStorage is the same as SessionStorage but it persists the data even when the browser is closed and reopened(i.e it has no expiration time) whereas in sessionStorage data gets cleared when the page session ends.

**[⬆ Back to Top](#table-of-contents)**

### How do you access web storage

The Window object implements the `WindowLocalStorage` and `WindowSessionStorage` objects which has `localStorage`(window.localStorage) and `sessionStorage`(window.sessionStorage) properties respectively. These properties create an instance of the Storage object, through which data items can be set, retrieved and removed for a specific domain and storage type (session or local).
For example, you can read and write on local storage objects as below

```javascript
localStorage.setItem("logo", document.getElementById("logo").value);
localStorage.getItem("logo");
```

**[⬆ Back to Top](#table-of-contents)**

### What are the methods available on session storage

The session storage provided methods for reading, writing and clearing the session data

```javascript
// Save data to sessionStorage
sessionStorage.setItem("key", "value");

// Get saved data from sessionStorage
let data = sessionStorage.getItem("key");

// Remove saved data from sessionStorage
sessionStorage.removeItem("key");

// Remove all saved data from sessionStorage
sessionStorage.clear();
```

**[⬆ Back to Top](#table-of-contents)**

### What is a higher order function

Higher-order function is a function that accepts another function as an argument or returns a function as a return value or both.

```javascript
const firstOrderFunc = () =>
  console.log("Hello, I am a First order function");
const higherOrder = (ReturnFirstOrderFunc) => ReturnFirstOrderFunc();
higherOrder(firstOrderFunc);
```

### What is a first order function

First-order function is a function that doesn’t accept another function as an argument and doesn’t return a function as its return value.

```javascript
const firstOrder = () => console.log("I am a first order function!");
```

**[⬆ Back to Top](#table-of-contents)**


### coding

### Create a button and onclick of the button the first time value should increment by 1 and at the second click value should  decrement by 1, default button value is 100

```js
import { useState } from "react";
import "./styles.css";

export default function App() {
  const [value, setvalue] = useState(100);
  
  const handleButtonClick = () => {
    if (value % 2 === 0) {
      setvalue((prevState) => prevState + 1);
    } else {
      setvalue((prevState) => prevState - 1);
    }

  };

  return (
    <div className="App">
      <h1>Hello CodeSandbox</h1>
      {value}
      <button onClick={handleButtonClick}> click me</button>
    </div>
  );
}
```

### Sum of amount from array object 
```js
let obj = [
  {id: 1, amount: 20},
  {id: 3, amount: 30},
  {id: 2, amount: 50}
]
const sumValues = obj.reduce((accumulator, object) => {
  return accumulator + object.amount;
}, 0);
console.log(sumValues)
```

### 3.	Fetch data from api, using function 
```js
async function getapi(){
    const response = await fetch(url);
    var data = await response.json();
    console.log(data, "data")
    // fetch(url)
    // .then(res => res.json())
    // .then(
    //   (data) => console.log(data, "daaata")
    // );
    }
  useEffect(()=> {
    getapi()
  })
```

### How to build a Roman Numeral to Integer Function in JavaScript

```js


const valArr = {
  I: 1,
  V: 5,
  X: 10,
  L: 50,
  C: 100,
  D: 500,
  M: 1000,
};
const s = "MCMLXXXXI";
// s = 1991
function romanToInt(s) {
  let accumulator = 0;
for (let i = 0; i < s.length; i++) {
    if (s[i] === "I" && s[i + 1] === "V") {
      accumulator += 4;
      i++;
    } else if (s[i] === "I" && s[i + 1] === "X") {
      accumulator += 9;
      i++;
    } else if (s[i] === "X" && s[i + 1] === "L") {
      accumulator += 40;
      i++;
    } else if (s[i] === "X" && s[i + 1] === "C") {
      accumulator += 90;
      i++;
    } else if (s[i] === "C" && s[i + 1] === "D") {
      accumulator += 400;
      i++;
    } else if (s[i] === "C" && s[i + 1] === "M") {
      accumulator += 900;
      i++;
    } else {
      accumulator += valArr[s[i]];
    }
  }
  return console.log(accumulator);
}

romanToInt(s)

```
