# My-JavaScript-Practice

Welcome to my JavaScript practice repository! 🚀 This repo contains my notes, examples, and implementations of key JavaScript concepts. The goal is to strengthen my understanding of the language, especially for interviews and real-world applications.

## Table of Contents

- [High-Order Functions (HOF)](#high-order-functions-hof)
- [Inheritance & Classes](#inheritance--classes)
- [Prototypal Inheritance](#prototypal-inheritance)
- [Call, Apply, Bind](#call-apply-bind)
- [Closures](#closures)
- [Closures in Action: Currying & Async](#closures-in-action-currying--async)
- [Event Loop](#event-loop)
- [Functions](#functions)
- [Map & Filter](#map--filter)
- [Pass by Value vs Pass by Reference](#pass-by-value-vs-pass-by-reference)
- [Polyfills](#polyfills)
- [Promises](#promises)
- [Prototype](#prototype)

---

## High-Order Functions (HOF)

A **higher-order function** is a function that either:
- Takes another function as an argument.
- Returns a function as its result.

Example:
```js
function greet(name) {
    return function(message) {
        console.log(`${message}, ${name}!`);
    };
}
const sayHello = greet("Alice");
sayHello("Hello"); // Output: Hello, Alice!
```

---

## Inheritance & Classes

JavaScript uses **ES6 classes** to implement inheritance more intuitively.

Example:
```js
class Animal {
    constructor(name) {
        this.name = name;
    }
    speak() {
        console.log(`${this.name} makes a noise.`);
    }
}
class Dog extends Animal {
    speak() {
        console.log(`${this.name} barks.`);
    }
}
const dog = new Dog("Buddy");
dog.speak(); // Output: Buddy barks.
```

---

## Prototypal Inheritance

JavaScript objects inherit properties from a prototype.

Example:
```js
function Person(name) {
    this.name = name;
}
Person.prototype.greet = function() {
    console.log(`Hello, my name is ${this.name}`);
};
const person1 = new Person("John");
person1.greet();
```

---

## Call, Apply, Bind

These methods allow changing `this` context in functions.

```js
function introduce(age) {
    console.log(`My name is ${this.name}, and I am ${age} years old.`);
}
const user = { name: "Alice" };
introduce.call(user, 25);
introduce.apply(user, [25]);
const boundFunc = introduce.bind(user, 25);
boundFunc();
```

---

## Closures

A **closure** is a function that remembers the variables from its outer scope even after the outer function has finished executing.

Example:
```js
function counter() {
    let count = 0;
    return function() {
        count++;
        console.log(count);
    };
}
const increment = counter();
increment(); // 1
increment(); // 2
```

---

## Closures in Action: Currying & Async

Currying:
```js
function add(x) {
    return function(y) {
        return x + y;
    };
}
console.log(add(5)(3)); // Output: 8
```

Handling Async with Closures:
```js
function fetchData(url) {
    return function(callback) {
        setTimeout(() => {
            callback(`Data from ${url}`);
        }, 1000);
    };
}
fetchData("api/data")((data) => console.log(data));
```

---

## Event Loop

JavaScript is single-threaded but handles async tasks efficiently using an **Event Loop**.

Example:
```js
console.log("Start");
setTimeout(() => console.log("Inside timeout"), 0);
console.log("End");
// Output: Start -> End -> Inside timeout
```

---

## Functions

Functions in JavaScript can be **declaration, expression, or arrow functions**.

Example:
```js
const add = (a, b) => a + b;
console.log(add(2, 3)); // 5
```

---

## Map & Filter

Map:
```js
const numbers = [1, 2, 3];
const squared = numbers.map(num => num * num);
console.log(squared); // [1, 4, 9]
```

Filter:
```js
const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // [2]
```

---

## Pass by Value vs Pass by Reference

- **Primitive types**: Passed by **value**.
- **Objects/Arrays**: Passed by **reference**.

Example:
```js
let a = 10;
let b = a;
b = 20;
console.log(a); // 10
```
```js
let obj1 = { x: 10 };
let obj2 = obj1;
obj2.x = 20;
console.log(obj1.x); // 20
```

---

## Polyfills

A polyfill is a script that adds functionality to older browsers.

Example: Custom `map()` implementation.
```js
Array.prototype.customMap = function(callback) {
    let result = [];
    for (let i = 0; i < this.length; i++) {
        result.push(callback(this[i], i, this));
    }
    return result;
};
```

---

## Promises

Promises help handle async operations.
```js
const myPromise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("Success!"), 2000);
});
myPromise.then(console.log);
```

---

## Prototype

Every object in JavaScript has a **prototype**.
```js
function Person(name) {
    this.name = name;
}
Person.prototype.sayHello = function() {
    console.log(`Hello, I'm ${this.name}`);
};
const john = new Person("John");
john.sayHello();
```

---

## Conclusion

This repo serves as my **JavaScript learning journey**. Feel free to explore the code, suggest improvements, or discuss concepts. Happy coding! 🚀

