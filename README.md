![Image of Javascript](img/js.png)

### 1) Principles of JavaScript

- When the javascript code runs, it:
  - Goes through the code line-by-line and runs/‘executes’  each line - known as the thread of execution
  - Saves ‘data’ like strings and arrays so we can use that data later - in its memory
  
We can even save code (‘functions’)


**Functions**

Code we save (‘define’) functions & can use (call/invoke/execute/run) later with the function’s name & ()

**Functions in javascript = first class object**

The can co-exit with and can be treated like any other javascript object
 
 1. Assigned to variables and properties of other objects
 2. Passed as argument into functions
 3. Returned as value from functions
 
For example

```javascript
const num = 3;

function multiplyBy2(inputNumber) {
  const result = inputNumber * 2;
  return result;
}

const output = multiplyBy2(num);
const newOutput = multiplyBy2(10);
```
1 . Initially variables and functions are stored in global memory

`
num: 3;
multiplyBy2: Function;
output: __
`

2 . puts `multiplyBy2(3)` in the Call stack

**Call stack**
- JavaScript keeps track of what function is currently running (where’s the thread of execution)
- Run a function - add to call stack 
- Finish running the function - JS removes it from call stack
- Whatever is stop of the call stack - that’s the function we’re currently running

```javascript
const output = multiplyBy2(num); //This `const output = multiplyBy2(num);` in `Execution context`
```

**Execution context**

Created and run the code of a function - has 2 parts
- [x] Thread of execution
- [x] Memory

```javascript
function multiplyBy2(inputNumber) {
  const result = inputNumber * 2;
  return result;
}
```
The photo below shows you how it works

![Image of Javascript](img/exc.png)

The same will happen on the following line: 
```javascript
const newOutput = multiplyBy2(10); //This `const newOutput = multiplyBy2(10);` in `Execution context`
```
![Image of Javascript](img/exc2.png)

----------------------------------------

### 2) Callbacks & Higher order functions

Why do we even have functions?

Let's see why ...

Create function 10 squared
- Takes no input
- Returns 10*10

What is the syntax (the exact code we type)?

```javascript
function tenSquared() {
  return 10 * 10;
}

tenSquared(); // 100
```
OK... What about a 9 squared function?

```javascript
function nineSquared() {
  return 9 * 9;
}

nineSquared(); // 81
```
And 8 squared function? 125 squared?

What principle are we breaking? - **DRY (Don't Repeat Yourself)** 
This is a fundamental principle in programming

We can generalize the function to make it reusable

```javascript
function squareNum(num) {
  return num * num;
}

squareNum(10); // 100
squareNum(9); // 81
squareNum(8); // 64
```

**Generalize functions**

‘Parameters’ (placeholders) mean we don’t need to decide what data to run our functionality on until we run the function
- Then provide an actual value (‘argument’) when we run the function

**Higher order functions follow same principle.**

We may not want to decide exactly what some of our functionality is until we run our function
- The outer function that takes in a function is our higher-order function
- The function we insert in our callback function (callback function)

**Higher-order functions**
- Takes in a function or passes out  function

Now suppose we have  function `copyArrayAndMultiplyBy2`

```javascript
function copyArrayAndMultiplyBy2(array) {
  const outer = [];
  for(let i = 0; i < array.length; i++) {
    outer.push(array[i] * 2);
  }
  return outer;
}

const myArray = [1,2,3];
const result = copyArrayAndMultiplyBy2(myArray);
```

What if want to copy array and divide by 2?

```javascript
function copyArrayAndDivideBy2(array) {
  const outer = [];
  for(let i = 0; i < array.length; i++) {
    outer.push(array[i] / 2);
  }
  return outer;
}

const myArray = [1,2,3];
const result = copyArrayAndDivideBy2(myArray);
```

This is really problematic...

must be a better way

We can generalize our function - so we pass in our specific instruction only when
we run **copyArrayAndManipulate**

```javascript
function copyArrayAndManipulate(array, instructions) {
  const outer = [];
  for(let i = 0; i < array.length; i++) {
    outer.push(instructions(array[i]));
  }
  return outer;
}


const result = copyArrayAndManipulate([1,2,3], input => input * 2);
```

**Callbacks and higher order functions simplify our code and keep it DRY**
- Declarative readable code: map, filter, reduce - the most readable way to write code to work with data
- Asynchronous JavaScript: callbacks are a core aspect of async JavaScript, and are under-the-hood of promises, async/await

Which is our Higher order function? - 
The outer function that takes in a function is our higher-order function.

Which is our Callback function? - 
The function we insert is our callback function

### 3) Closure (scope and execution context)
Soon...
### 4) Asynchronous javascript & the event loop
Soon...
### 5) Classes & Prototypes (OOP)
Soon..
