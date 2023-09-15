# Javascript-questions

---


### Table of Contents


| No. | Questions | No | Questions |
| ----- | ------------------- | ---- | ------------------- |
| 1 | [What is scope in javascript](#1) | | |
| 2 | [What are the differences between primitives and non-primitives?](#2) | | |
| 3 | [What is the difference between null and undefined](#3) | | |
| 4 | [What is the difference between == and === operators](#4) | | |
| 5 | [What is a proto and prototype](#5) | | |
| 6 | [What is Event Loop / call stack/ event queue](#6) | | |
| 7 | [](#7) | | |
| 8 | [](#8) | | |
| 9 | [](#9) | | |
| 10| [](#10) | | |


### 1
### What is scope in javascript
Scope is the accessibility of variables, functions, and objects in some particular part of your code during runtime. In other words, scope determines the visibility of variables and other resources in areas of your code.


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
**[⬆ Back to Top](#table-of-contents)**

**[⬆ Back to Top](#table-of-contents)**
