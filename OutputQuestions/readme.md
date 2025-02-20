Here’s a set of **25 new practice questions** focused on **arrays**, **strings**, and **objects**, designed to help you get more comfortable with these concepts!

### **Arrays (10 Questions)**  
1. Create an array of 6 different fruits and log it.  
2. Access the third element of an array and log it.  
3. Use `.push()` to add a new element to the end of an array.  
4. Use `.pop()` to remove the last element of an array and log the updated array.  
5. Write a program to create a sub-array of elements from index 2 to 5.  
6. Reverse an array without using `.reverse()` method.  
7. Use `.filter()` to create a new array of only even numbers from the array [1, 2, 3, 4, 5, 6].  
8. Write a function that accepts an array and returns the average of its elements.  
9. Combine two arrays `[7, 8, 9]` and `[10, 11]` using the spread operator.  
10. Write a program that checks if two arrays are identical.

### **Strings (10 Questions)**  
11. Write a program that accepts a string and logs its length.  
12. Create a function that checks if a string contains the word “JavaScript”.  
13. Write a program that converts a string to uppercase.  
14. Create a function that accepts a string and returns the number of vowels in it.  
15. Use `.split()` to convert a string `"apple,banana,orange"` into an array.  
16. Write a program that reverses a string without using the `.reverse()` method.  
17. Create a function that removes all spaces from a string.  
18. Check if a string is a palindrome (reads the same forward and backward).  
19. Create a function that returns the first letter of each word in a string.  
20. Write a program that replaces all occurrences of "cat" with "dog" in a string.

### **Objects (5 Questions)**  
21. Create an object to represent a book with properties like `title`, `author`, and `pages`. Log the object.  
22. Write a program that changes the value of a property in an object.  
23. Write a function that accepts an object and logs all its keys.  
24. Create an object representing a car and then add a `color` property to it.  
25. Write a function that checks if an object has a specific property and logs a message based on the result.  

Would you like to dive into any of these with step-by-step solutions or more detailed explanations?





---

### **Question 1: Hoisting and Lexical Scope**

```javascript
function foo() {
    console.log(x);
    var x = 10;
    console.log(x);
}

foo();
console.log(x);
```

**What will the output be and why? Explain how hoisting works here.**

---

### **Question 2: Closures & Lexical Scope**

```javascript
function outer() {
    let outerVar = 'I am from outer';

    function inner() {
        console.log(outerVar);
    }

    return inner;
}

let closureFunction = outer();
closureFunction();
outerVar = 'Modified outer variable';
closureFunction();
```

**What will be the output here? How does closure behave in this case?**

---

### **Question 3: Event Loop & Microtasks/Macrotasks**

```javascript
console.log('Start');

setTimeout(() => {
    console.log('Timeout 1');
}, 0);

Promise.resolve().then(() => {
    console.log('Promise 1');
});

setTimeout(() => {
    console.log('Timeout 2');
}, 0);

Promise.resolve().then(() => {
    console.log('Promise 2');
});

console.log('End');
```

**Explain the output step by step. Why does this happen in this particular order?**

---

### **Question 4: Prototypal Inheritance**

```javascript
function Animal() {
    this.species = 'Animal';
}

Animal.prototype.sayHi = function() {
    console.log('Hi from Animal');
};

function Dog() {
    this.breed = 'Bulldog';
}

Dog.prototype = new Animal();

const dog = new Dog();
dog.sayHi();
console.log(dog.species);
```

**What is the output here? Why is `dog.species` accessible even though it's not explicitly defined in the `Dog` constructor? How does prototypal inheritance work in this case?**

---

### **Question 5: Execution Context & Call Stack**

```javascript
function a() {
    b();
    console.log('a');
}

function b() {
    c();
    console.log('b');
}

function c() {
    console.log('c');
}

a();
```

**What is the order of the output here? Explain how the call stack behaves during the execution of this code.**

---

### **Question 6: `call`, `apply`, and `bind`**

```javascript
function greet(name) {
    console.log(`Hello, ${name}`);
}

const person = {
    name: 'John'
};

greet.call(person, 'Mike');
greet.apply(person, ['Sarah']);
const greetBound = greet.bind(person, 'Alice');
greetBound();
```

**What will be the output of this code and why? Explain the difference between `call`, `apply`, and `bind` in this context.**

---

### **Question 7: `setTimeout` and `setInterval` behavior with `useEffect`**

```javascript
import React, { useState, useEffect } from 'react';

function TimerComponent() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        const intervalId = setInterval(() => {
            setCount(c => c + 1);
            console.log('Interval:', count);
        }, 1000);

        return () => clearInterval(intervalId);
    }, []);

    return <div>Count: {count}</div>;
}

export default TimerComponent;
```

**What will the output be and why? How do `setInterval` and the closure work here in relation to React's state updates?**

---

### **Question 8: Debouncing & Throttling**

```javascript
const debounce = (func, delay) => {
    let timeout;
    return function(...args) {
        clearTimeout(timeout);
        timeout = setTimeout(() => {
            func(...args);
        }, delay);
    };
};

const throttle = (func, delay) => {
    let lastCall = 0;
    return function(...args) {
        const now = new Date().getTime();
        if (now - lastCall >= delay) {
            lastCall = now;
            func(...args);
        }
    };
};

const log = (message) => {
    console.log(message);
};

const debouncedLog = debounce(log, 2000);
const throttledLog = throttle(log, 2000);

// Trigger events at varying intervals
debouncedLog('Debounced message 1');
debouncedLog('Debounced message 2');
setTimeout(() => debouncedLog('Debounced message 3'), 1000);
setTimeout(() => debouncedLog('Debounced message 4'), 3000);

throttledLog('Throttled message 1');
throttledLog('Throttled message 2');
setTimeout(() => throttledLog('Throttled message 3'), 1000);
setTimeout(() => throttledLog('Throttled message 4'), 3000);
```

**What will be the output of the debounced and throttled logs? Explain how debouncing and throttling differ and how they work in this scenario.**

---

### **Question 9: Complex Object Manipulation**

```javascript
const data = [
    { id: 1, name: 'John', active: true },
    { id: 2, name: 'Jane', active: false },
    { id: 3, name: 'Tom', active: true },
    { id: 4, name: 'Jerry', active: false },
];

const result = data
    .filter((person) => person.active)
    .map((person) => person.name)
    .reduce((acc, name) => acc + ', ' + name);

console.log(result);
```

**What will the output be and explain how `filter`, `map`, and `reduce` work here?**

---

### **Question 10: Edge Case with Async and Callbacks**

```javascript
function getData(callback) {
    setTimeout(() => {
        callback('Data fetched');
    }, 1000);
}

console.log('Start');

getData((data) => {
    console.log(data);
});

console.log('End');
```

**What will the output be and why? How does the async nature of `setTimeout` affect the order of the logs?**

---


### **Question 11: Hoisting with `let`, `const`, and `var`**

```javascript
console.log(foo);
var foo = 1;
console.log(bar);
let bar = 2;

function test() {
    console.log(baz);
    const baz = 3;
}

test();
```

**What will the output be? Why does the `let` and `const` behave differently compared to `var` in this scenario?**

---

### **Question 12: Closure with `setTimeout`**

```javascript
function createTimeouts() {
    for (var i = 0; i < 3; i++) {
        setTimeout(() => {
            console.log(i);
        }, 1000);
    }
}

createTimeouts();
```

**What will the output be? What is happening inside the `setTimeout`? Why does `i` always print as the same number, and how can this issue be fixed?**

---

### **Question 13: `bind` and `this` context**

```javascript
const person = {
    firstName: 'John',
    lastName: 'Doe',
    getFullName: function() {
        return this.firstName + ' ' + this.lastName;
    }
};

const anotherPerson = {
    firstName: 'Jane',
    lastName: 'Smith'
};

const getFullNameForAnotherPerson = person.getFullName.bind(anotherPerson);
console.log(getFullNameForAnotherPerson());
```

**What is the output here, and why does using `bind` affect the `this` context? Explain how `bind` works in this case.**

---

### **Question 14: Event Loop with `setTimeout` and `Promise`**

```javascript
console.log('Start');

setTimeout(() => {
    console.log('Timeout 1');
}, 0);

Promise.resolve().then(() => {
    console.log('Promise 1');
});

setTimeout(() => {
    console.log('Timeout 2');
}, 0);

Promise.resolve().then(() => {
    console.log('Promise 2');
});

console.log('End');
```

**What is the expected output, and how does the JavaScript event loop process the code with respect to microtasks and macrotasks?**

---

### **Question 15: Prototypal Inheritance and Method Overriding**

```javascript
function Vehicle() {
    this.type = 'Vehicle';
}

Vehicle.prototype.move = function() {
    console.log('Moving...');
};

function Car() {
    this.model = 'Sedan';
}

Car.prototype = new Vehicle();

Car.prototype.move = function() {
    console.log('Car is moving...');
};

const myCar = new Car();
myCar.move();
console.log(myCar.type);
```

**What is the output here? Why does `myCar.move()` invoke the overridden `move` method and not the one from `Vehicle`? How does method overriding in the prototype chain work?**

---

### **Question 16: `async/await` with error handling**

```javascript
async function fetchData() {
    let response = await fetch('https://api.example.com/data');
    return response.json();
}

fetchData().then(data => {
    console.log(data);
}).catch(err => {
    console.log('Error:', err);
});
```

**What happens if the fetch request fails or if the API does not return JSON? How does `async/await` handle errors, and how does `.catch()` behave in this scenario?**

---

### **Question 17: Deep Equality of Objects**

```javascript
const obj1 = { name: 'John', details: { age: 30, city: 'New York' } };
const obj2 = { name: 'John', details: { age: 30, city: 'New York' } };

console.log(obj1 === obj2); // true or false?
console.log(JSON.stringify(obj1) === JSON.stringify(obj2)); // true or false?
```

**What is the output of the above comparisons, and why does comparing objects using `===` or `JSON.stringify()` behave differently?**

---

### **Question 18: Array Destructuring and Spread Operator**

```javascript
const arr1 = [1, 2, 3, 4];
const arr2 = [...arr1];

arr2[0] = 10;

console.log(arr1);
console.log(arr2);
```

**What is the output? What happens with the spread operator in terms of shallow vs deep copying of arrays?**

---

### **Question 19: Memoization and Caching**

```javascript
function memoize(fn) {
    const cache = {};
    return function(...args) {
        const key = JSON.stringify(args);
        if (cache[key]) {
            console.log('Cache hit');
            return cache[key];
        }
        console.log('Cache miss');
        const result = fn(...args);
        cache[key] = result;
        return result;
    };
}

const add = (a, b) => a + b;

const memoizedAdd = memoize(add);

console.log(memoizedAdd(1, 2));
console.log(memoizedAdd(1, 2));
console.log(memoizedAdd(2, 3));
```

**What is the output? How does memoization improve performance in this case, and what potential issues might arise from this approach?**

---

### **Question 20: `setInterval` with React's `useEffect` and State Updates**

```javascript
import React, { useState, useEffect } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        const interval = setInterval(() => {
            setCount(count + 1);
            console.log(count);
        }, 1000);

        return () => clearInterval(interval);
    }, [count]);

    return <div>Count: {count}</div>;
}

export default Counter;
```

**What happens here and why? Does the `setInterval` function behave as expected with state updates in React? How does React's `useEffect` interact with state in this case, and why might there be unexpected behavior?**

---


### **Question 1: `setTimeout` and `useEffect` in React with Closure**

```javascript
import React, { useState, useEffect } from 'react';

function Timer() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        setTimeout(() => {
            setCount(count + 1);
        }, 1000);
    }, []);

    return <div>Count: {count}</div>;
}

export default Timer;
```

**What is the output here, and why doesn’t the count increment as expected? Explain the behavior of `setTimeout` in relation to the closure in `useEffect`.**

---

### **Question 2: `setTimeout` Inside `useEffect` with Dependency Array**

```javascript
import React, { useState, useEffect } from 'react';

function TimerComponent() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        const timer = setTimeout(() => {
            setCount(count + 1);
            console.log('Timeout executed');
        }, 1000);

        return () => clearTimeout(timer); // Cleanup on unmount or dependency change
    }, [count]);

    return <div>Count: {count}</div>;
}

export default TimerComponent;
```

**What will happen here? Will the timeout be reset on every render? Why?**

---

### **Question 3: Event Loop and `setTimeout` with Multiple Calls**

```javascript
console.log('Start');

setTimeout(() => {
    console.log('Timeout 1');
}, 0);

setTimeout(() => {
    console.log('Timeout 2');
}, 0);

console.log('End');
```

**What will be the output, and why do the `setTimeout` callbacks execute in that order? Explain how the event loop handles these callbacks.**

---

### **Question 4: Multiple `setTimeout` Calls with Delays in `useEffect`**

```javascript
import React, { useState, useEffect } from 'react';

function App() {
    const [status, setStatus] = useState('Started');

    useEffect(() => {
        setTimeout(() => {
            setStatus('Processing');
        }, 1000);

        setTimeout(() => {
            setStatus('Completed');
        }, 500);

        return () => {
            console.log('Cleanup');
        };
    }, []);

    return <div>{status}</div>;
}

export default App;
```

**What will the output be and why? How does the sequence of `setTimeout` work in relation to the `status` update in the component?**

---

### **Question 5: `useEffect` with Multiple `setTimeout` Updates**

```javascript
import React, { useState, useEffect } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        setTimeout(() => {
            setCount(count + 1);
        }, 1000);

        setTimeout(() => {
            setCount(count + 2);
        }, 2000);
    }, []);

    return <div>Count: {count}</div>;
}

export default Counter;
```

**What will be the output? Why doesn’t React update the count as expected, and how does the closure of `setTimeout` affect the `count` value in this example?**

---

### **Question 6: Event Loop with `setTimeout` and `Promise`**

```javascript
console.log('Start');

setTimeout(() => {
    console.log('Timeout');
}, 0);

Promise.resolve().then(() => {
    console.log('Promise');
});

console.log('End');
```

**What is the output, and why does `Promise` appear before the `setTimeout` callback in the event loop, even though both are executed asynchronously?**

---

### **Question 7: `setTimeout` Behavior in React’s `useEffect` Hook with State**

```javascript
import React, { useState, useEffect } from 'react';

function App() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        const timer = setTimeout(() => {
            setCount(count + 1);
        }, 1000);

        return () => clearTimeout(timer);
    }, [count]);

    return <div>Count: {count}</div>;
}

export default App;
```

**What will the output be? How does the `useEffect` cleanup and `setTimeout` interaction work with state updates? Why might this cause an infinite loop or unexpected behavior?**

---

### **Question 8: `setTimeout` in React with Delayed Component Unmount**

```javascript
import React, { useState, useEffect } from 'react';

function Timer() {
    const [isMounted, setIsMounted] = useState(true);

    useEffect(() => {
        const timeoutId = setTimeout(() => {
            console.log('Timeout triggered after delay');
        }, 3000);

        return () => {
            clearTimeout(timeoutId);
            console.log('Cleanup executed');
        };
    }, []);

    return (
        <div>
            <button onClick={() => setIsMounted(false)}>Unmount</button>
            {isMounted && <div>Component is Mounted</div>}
        </div>
    );
}

export default Timer;
```

**What will be the output when you click on the "Unmount" button? How does React handle the `setTimeout` when the component is unmounted?**

---

### **Question 9: Delayed State Updates with `setTimeout` and `useEffect`**

```javascript
import React, { useState, useEffect } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        setTimeout(() => {
            setCount(count + 1);
            console.log('State updated to:', count + 1);
        }, 2000);
    }, [count]);

    return <div>Count: {count}</div>;
}

export default Counter;
```

**What will be the output? Explain why the count is not updated immediately after 2 seconds, and how React handles state and closure in this `useEffect`.**

---

### **Question 10: Using `setTimeout` with `useEffect` in a Loop**

```javascript
import React, { useState, useEffect } from 'react';

function Timer() {
    const [seconds, setSeconds] = useState(0);

    useEffect(() => {
        let intervalId;

        const startTimer = () => {
            intervalId = setTimeout(() => {
                setSeconds(prev => prev + 1);
                startTimer();  // recursive call to continue the timer
            }, 1000);
        };

        startTimer();

        return () => clearTimeout(intervalId);
    }, []);

    return <div>Seconds: {seconds}</div>;
}

export default Timer;
```

**What will happen here? Will the timer continue indefinitely, or is there something that could cause issues in terms of state updates? Explain the behavior of `setTimeout` in the recursive function inside `useEffect`.**

---



Great! Let's dive into some tricky questions on **Array Methods**. These will test your understanding of how to manipulate arrays in JavaScript, handle different edge cases, and optimize the use of array methods. Here are 10 advanced questions on the topics you've mentioned:

---

### **Question 1: `map()` vs. `forEach()`**

```javascript
const arr = [1, 2, 3, 4];

const result1 = arr.map((x) => x * 2);
const result2 = arr.forEach((x) => x * 2);

console.log(result1);
console.log(result2);
```

**What is the output here, and why is `result2` different from `result1`? Explain the key differences between `map()` and `forEach()`.**

---

### **Question 2: `filter()` and Edge Case**

```javascript
const arr = [1, 2, 3, 4, 5];

const result = arr.filter((x) => x % 2 === 0 && x > 2);
console.log(result);
```

**What will the output be? What will happen if the filtering condition changes to `x % 2 === 0 || x > 2`?**

---

### **Question 3: Using `reduce()` for Array Transformation**

```javascript
const arr = [1, 2, 3, 4];

const result = arr.reduce((acc, currentValue) => {
    if (currentValue % 2 === 0) {
        acc.push(currentValue * 2);
    }
    return acc;
}, []);

console.log(result);
```

**What will be the output, and how does `reduce()` work here to achieve array transformation?**

---

### **Question 4: `find()` vs. `filter()`**

```javascript
const arr = [10, 20, 30, 40, 50];

const result1 = arr.find((x) => x > 25);
const result2 = arr.filter((x) => x > 25);

console.log(result1);
console.log(result2);
```

**What is the output, and how does `find()` differ from `filter()`? Why does `find()` return a single value, and `filter()` returns an array?**

---

### **Question 5: `some()` vs. `every()`**

```javascript
const arr = [1, 2, 3, 4, 5];

const result1 = arr.some((x) => x > 3);
const result2 = arr.every((x) => x > 3);

console.log(result1);
console.log(result2);
```

**What is the output, and what is the difference between `some()` and `every()` in terms of condition checks?**

---

### **Question 6: `sort()` with Custom Comparator**

```javascript
const arr = [5, 2, 8, 3, 1, 7];

arr.sort((a, b) => {
    return a > b ? 1 : a < b ? -1 : 0;
});

console.log(arr);
```

**What will the output be? Explain how `sort()` with a custom comparator works. What could go wrong if you omit the custom comparator function?**

---

### **Question 7: `reverse()`**

```javascript
const arr = [1, 2, 3, 4];

arr.reverse();

console.log(arr);
```

**What will the output be after calling `reverse()`? Explain how `reverse()` affects the original array. Does it mutate the array or return a new one?**

---

### **Question 8: `slice()` vs. `splice()`**

```javascript
const arr = [10, 20, 30, 40, 50];

const result1 = arr.slice(1, 3);
const result2 = arr.splice(1, 3);

console.log(result1);
console.log(result2);
console.log(arr);
```

**What is the output of `slice()` and `splice()`? What is the key difference between `slice()` and `splice()`? How do they affect the original array?**

---

### **Question 9: `flat()` & `flatMap()`**

```javascript
const arr = [1, [2, 3], [4, 5]];

const flatResult = arr.flat();
const flatMapResult = arr.flatMap((x) => x);

console.log(flatResult);
console.log(flatMapResult);
```

**What will be the output, and what’s the difference between `flat()` and `flatMap()`? In which case would you prefer one over the other?**

---

### **Question 10: `reduceRight()`**

```javascript
const arr = [1, 2, 3, 4];

const result = arr.reduceRight((acc, currentValue) => acc + currentValue, 0);

console.log(result);
```

**What is the output of `reduceRight()`? How does it differ from `reduce()` in terms of order of iteration? When might `reduceRight()` be useful?**

---

### **Bonus: Searching with `includes()`, `indexOf()`, and `lastIndexOf()`**

```javascript
const arr = [1, 2, 3, 4, 3, 5];

console.log(arr.includes(3));         // true or false?
console.log(arr.indexOf(3));          // first occurrence index?
console.log(arr.lastIndexOf(3));      // last occurrence index?
```

**What will be the output of these methods? How does each of these methods behave differently when searching for an element in the array?**


---

### **Object Manipulation Questions**

---

### **Question 1: `Object.keys()`, `Object.values()`, `Object.entries()`**

```javascript
const obj = {
    a: 1,
    b: 2,
    c: 3
};

const keys = Object.keys(obj);
const values = Object.values(obj);
const entries = Object.entries(obj);

console.log(keys);   // ['a', 'b', 'c']
console.log(values); // [1, 2, 3]
console.log(entries); // [['a', 1], ['b', 2], ['c', 3]]
```

**How would you transform `entries` back into an object? What would happen if you mistakenly used `Object.keys()` on an object with a prototype chain?**

---

### **Question 2: `Object.assign()` vs. Spread Operator**

```javascript
const obj1 = { name: 'Alice', age: 25 };
const obj2 = { city: 'New York', country: 'USA' };

const merged1 = Object.assign({}, obj1, obj2);
const merged2 = { ...obj1, ...obj2 };

console.log(merged1);
console.log(merged2);
```

**What is the difference between `Object.assign()` and the spread operator in this case? Are there any key differences in behavior when dealing with nested objects or arrays?**

---

### **Question 3: Deep Copy vs. Shallow Copy**

```javascript
const originalObj = { name: 'Bob', address: { city: 'Paris', country: 'France' } };

const shallowCopy = Object.assign({}, originalObj);
const deepCopy = JSON.parse(JSON.stringify(originalObj));

originalObj.address.city = 'London';

console.log(originalObj.address.city);  // London
console.log(shallowCopy.address.city);  // London
console.log(deepCopy.address.city);     // Paris
```

**Explain the behavior of shallow copy vs deep copy here. How does `structuredClone()` work as an alternative to `JSON.parse/stringify`?**

---

### **Question 4: Merging Objects**

```javascript
const obj1 = { a: 1, b: 2 };
const obj2 = { b: 3, c: 4 };

const merged = { ...obj1, ...obj2 };
console.log(merged);
```

**What will be the output here? How does JavaScript handle key conflicts when merging two objects?**

---

### **Question 5: Deleting Object Properties**

```javascript
const person = {
    name: 'John',
    age: 30,
    city: 'New York'
};

delete person.city;

console.log(person);
```

**What is the output after `delete person.city`? What happens when you attempt to delete a property that does not exist?**

---

### **Question 6: Optional Chaining and Nullish Coalescing**

```javascript
const user = { profile: { name: 'Jane' } };

console.log(user?.profile?.name);     // 'Jane'
console.log(user?.profile?.age ?? 25); // 25
```

**What is the behavior of optional chaining (`?.`) and nullish coalescing (`??`) in this example? How do they handle `undefined` or `null` values differently from regular logical operators?**

---

### **Question 7: Computed Property Names**

```javascript
const key = 'color';
const obj = {
    [key]: 'red',
    ['size']: 'medium'
};

console.log(obj);
```

**What is the output here? How do computed property names work in object literals?**

---

---

### **String Manipulation Questions**

---

### **Question 8: `split()` and `join()`**

```javascript
const str = 'apple,banana,orange';
const arr = str.split(',');

console.log(arr);              // ['apple', 'banana', 'orange']
console.log(arr.join('-'));    // 'apple-banana-orange'
```

**How do `split()` and `join()` work, and what happens if you use a separator that is not present in the string or array?**

---

### **Question 9: `replace()`, `replaceAll()`, and `match()`**

```javascript
const sentence = 'The cat and the cat';
const newSentence1 = sentence.replace('cat', 'dog');
const newSentence2 = sentence.replaceAll('cat', 'dog');
const matches = sentence.match(/cat/g);

console.log(newSentence1);  // The dog and the cat
console.log(newSentence2);  // The dog and the dog
console.log(matches);       // ['cat', 'cat']
```

**What are the differences between `replace()`, `replaceAll()`, and `match()`? When would you use each of these methods?**

---

### **Question 10: `trim()`, `padStart()`, and `padEnd()`**

```javascript
const str = '  Hello, World!  ';

console.log(str.trim());           // 'Hello, World!'
console.log(str.padStart(20, '*')); // '****Hello, World!  '
console.log(str.padEnd(20, '*'));   // '  Hello, World!****'
```

**How do `trim()`, `padStart()`, and `padEnd()` work? What happens when you try to pad a string shorter than the given length?**

---

### **Question 11: `toUpperCase()` and `toLowerCase()`**

```javascript
const str = 'JavaScript';

console.log(str.toUpperCase()); // 'JAVASCRIPT'
console.log(str.toLowerCase()); // 'javascript'
```

**What is the difference between `toUpperCase()` and `toLowerCase()`? Are they case-sensitive when dealing with different languages or special characters?**

---

---

### **Destructuring & Rest/Spread Operators Questions**

---

### **Question 12: Array Destructuring**

```javascript
const arr = [1, 2, 3, 4, 5];
const [first, second, ...rest] = arr;

console.log(first);   // 1
console.log(second);  // 2
console.log(rest);    // [3, 4, 5]
```

**What happens when using array destructuring with the rest operator? What if the array has fewer elements than expected?**

---

### **Question 13: Object Destructuring with Default Values**

```javascript
const obj = { name: 'Alice', age: 30 };

const { name, age, country = 'USA' } = obj;

console.log(name);    // 'Alice'
console.log(country); // 'USA'
```

**What happens if a property is missing during object destructuring? Explain the default value behavior in this case.**

---

### **Question 14: Swapping Variables Using Destructuring**

```javascript
let a = 5;
let b = 10;

[a, b] = [b, a];

console.log(a); // 10
console.log(b); // 5
```

**How does destructuring work to swap variables in this case? Are there any edge cases to watch out for when using this method?**

---

---

### **Set & Map Questions**

---

### **Question 15: Using `Set` Methods**

```javascript
const mySet = new Set([1, 2, 3, 4]);

mySet.add(5);
mySet.add(1); // Duplicate value

console.log(mySet.has(3));  // true
console.log(mySet.size);    // 5
console.log(mySet);         // Set { 1, 2, 3, 4, 5 }
```

**What happens when you try to add a duplicate value to a `Set`? Explain how `Set` handles uniqueness and size.**

---

### **Question 16: Using `Map` Methods**

```javascript
const myMap = new Map();
myMap.set('name', 'Alice');
myMap.set('age', 30);

console.log(myMap.get('name'));  // 'Alice'
console.log(myMap.size);         // 2
myMap.delete('age');
console.log(myMap.size);         // 1
```

**What happens when you use the `set()`, `get()`, and `delete()` methods on a `Map`? How does the `Map` maintain the insertion order of keys?**

---

### **Question 17: Converting Between Arrays and Sets/Maps**

```javascript
const arr = [1, 2, 3, 4];
const uniqueSet = new Set(arr);
const mapFromArr = new Map(arr.map(x => [x, x * 2]));

console.log(Array.from(uniqueSet)); // [1, 2, 3, 4]
console.log(Array.from(mapFromArr)); // [[1, 2], [2, 4], [3, 6], [4, 8]]
```

**How do you convert between arrays, sets, and maps? What happens if you try to convert an object directly into a `Set` or `Map`?**

---


### **Tricky Array and Object Questions**

---

### **Question 1: Array Mutation and Immutability**

```javascript
const arr = [1, 2, 3, 4];
const arrCopy = arr;

arrCopy[0] = 10;

console.log(arr);      // What will this log?
console.log(arrCopy);  // What will this log?
```

**Why does `arr` get mutated even though we assigned it to `arrCopy`? What is the difference between shallow copies and deep copies in the context of arrays? How would you fix this to avoid mutating the original array?**

---

### **Question 2: Array and Object Reference Behavior**

```javascript
const obj1 = { key: 'value' };
const obj2 = obj1;

obj2.key = 'new value';

console.log(obj1); // What will this log?
console.log(obj2); // What will this log?
```

**Why does `obj1` change when `obj2.key` is modified? What’s the underlying behavior of JavaScript objects when they are assigned to each other?**

---

### **Question 3: Destructuring Nested Objects with Renaming**

```javascript
const person = {
    name: 'Alice',
    details: {
        age: 30,
        city: 'New York'
    }
};

const { details: { age, city: hometown } } = person;

console.log(age);      // What will this log?
console.log(hometown); // What will this log?
```

**Can you explain how destructuring works with nested objects? What would happen if the `details` property did not exist on the `person` object?**

---

### **Question 4: Array `map()` vs `forEach()` Mutation**

```javascript
const arr = [1, 2, 3, 4];

arr.map((el, index) => {
    arr[index] = el * 2;
});

console.log(arr);
```

**What will the output be? Why is this behavior different from `map()`’s usual output? How would you modify the code to prevent mutating the original array?**

---

### **Question 5: Spread Operator with Nested Objects**

```javascript
const obj1 = { name: 'John', address: { city: 'Paris' } };
const obj2 = { ...obj1, address: { city: 'London' } };

console.log(obj1.address.city);  // What will this log?
console.log(obj2.address.city);  // What will this log?
```

**Why does changing the `address` property in `obj2` not affect `obj1`? Does the spread operator perform a shallow or deep copy in this case? How would you make a deep copy of `obj1`?**

---

### **Question 6: Object Property Order in `for...in` Loop**

```javascript
const obj = {
    b: 2,
    a: 1,
    c: 3
};

for (let key in obj) {
    console.log(key);
}
```

**What will be the order of the keys logged? Is there a guaranteed order when iterating over object properties in JavaScript? How can you ensure properties are logged in a specific order?**

---

### **Question 7: Array `reduce()` with Early Exit**

```javascript
const arr = [1, 2, 3, 4, 5];

const result = arr.reduce((acc, cur) => {
    if (cur > 3) return acc;
    return acc + cur;
}, 0);

console.log(result);
```

**What will the output be? Why does `reduce()` not stop even if the condition inside the callback is met? What would be a way to break out of `reduce()` early?**

---

### **Question 8: Object Destructuring with Default Values**

```javascript
const user = { name: 'Charlie' };

const { name, age = 25, city = 'Unknown' } = user;

console.log(name);  // What will this log?
console.log(age);   // What will this log?
console.log(city);  // What will this log?
```

**What happens when the destructuring assignment does not find the `age` and `city` properties in the object? How does JavaScript handle default values in this case?**

---

### **Question 9: Spread Operator with Arrays of Objects**

```javascript
const arr1 = [{ name: 'John' }, { name: 'Alice' }];
const arr2 = [...arr1];

arr2[0].name = 'Bob';

console.log(arr1[0].name);  // What will this log?
console.log(arr2[0].name);  // What will this log?
```

**Why does modifying an element in `arr2` also modify `arr1`? What happens when you try to spread an array of objects in JavaScript? How can you fix this to avoid mutation of the original array?**

---

### **Question 10: Object Constructor and Prototype Chain**

```javascript
function Person(name) {
    this.name = name;
}

const person1 = new Person('Alice');
const person2 = new Person('Bob');

Person.prototype.sayHello = function () {
    return `Hello, ${this.name}!`;
};

console.log(person1.sayHello()); // What will this log?
console.log(person2.sayHello()); // What will this log?
```

**How does the prototype chain work in this case? What would happen if `sayHello()` was a method on `person1` rather than the prototype?**

---

### **Question 11: Arrays with `find()` and Mutation**

```javascript
const arr = [1, 2, 3, 4, 5];

const found = arr.find((el) => el > 3);

console.log(found);   // What will this log?
console.log(arr);     // What will this log?
```

**Does `find()` mutate the original array? What is the expected behavior of `find()` with respect to array mutation? How can you prevent mutation in such cases?**

---

### **Question 12: Dynamic Object Property Assignment**

```javascript
const obj = {};

for (let i = 0; i < 3; i++) {
    obj[`key${i}`] = `value${i}`;
}

console.log(obj);
```

**What will be the resulting object? How does JavaScript handle dynamically assigned keys? Can you think of cases where this dynamic assignment could cause issues (e.g., overwriting existing properties)?**

---

### **Question 13: Object Methods and `this` Context**

```javascript
const obj = {
    name: 'Alice',
    greet: function () {
        console.log(this.name);
    }
};

const obj2 = {
    name: 'Bob'
};

obj.greet.call(obj2); // What will this log?
```

**Why does using `call()` change the `this` context? What will be the output of `obj.greet.call(obj2)`? Can you use `apply()` or `bind()` instead of `call()` here?**

---

### **Question 14: Handling Arrays with `map()`, `filter()`, and `reduce()`**

```javascript
const arr = [1, 2, 3, 4, 5];

const result = arr.map((x) => x * 2).filter((x) => x > 5).reduce((acc, x) => acc + x, 0);

console.log(result);
```

**How do `map()`, `filter()`, and `reduce()` work together in this chain? What will the output be? Explain the intermediate steps in detail.**

---

### **Question 15: Destructuring with Nested Arrays and Default Values**

```javascript
const arr = [1, [2, 3], 4];

const [first, [second, third = 5], fourth] = arr;

console.log(first);   // What will this log?
console.log(second);  // What will this log?
console.log(third);   // What will this log?
console.log(fourth);  // What will this log?
```

**How does destructuring work with nested arrays and default values? What happens if the nested array doesn't provide the expected values?**

---

### **Bonus: Object Merge with `Object.assign()` and Spread Operator**

```javascript
const obj1 = { a: 1, b: 2 };
const obj2 = { b: 3, c: 4 };

const merged1 = Object.assign({}, obj1, obj2);
const merged2 = { ...obj1, ...obj2 };

console.log(merged1);
console.log(merged2);
```

**What is the difference between `Object.assign()` and the spread operator when merging objects? Do they behave the same? How do they handle nested objects and arrays?**

---

---

### **Tricky Questions on Promises & Async/Await**

---

### **Question 1: Promise Chaining with `.then()`, `.catch()`, and `.finally()`**

```javascript
function asyncFunction() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("Success");
        }, 1000);
    });
}

asyncFunction()
    .then((result) => {
        console.log(result);  // "Success"
        return "Chained result";
    })
    .catch((error) => {
        console.log(error);
    })
    .finally(() => {
        console.log("Finally block executed");
    });
```

**What will be the output of this code? How does the `.finally()` block behave in comparison to `.then()` and `.catch()`?**

---

### **Question 2: Handling Errors in Promises with `.catch()`**

```javascript
function failingFunction() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            reject("Failed");
        }, 500);
    });
}

failingFunction()
    .then((result) => {
        console.log(result);
    })
    .catch((error) => {
        console.log(error);  // "Failed"
    });
```

**How does `.catch()` handle errors in promises? What happens if `.catch()` is omitted in the promise chain, and an error is thrown?**

---

### **Question 3: Promise.all() with Multiple Promises**

```javascript
const promise1 = new Promise((resolve, reject) => {
    setTimeout(() => resolve('First'), 200);
});

const promise2 = new Promise((resolve, reject) => {
    setTimeout(() => resolve('Second'), 100);
});

const promise3 = new Promise((resolve, reject) => {
    setTimeout(() => resolve('Third'), 300);
});

Promise.all([promise1, promise2, promise3])
    .then((results) => {
        console.log(results); // What will be logged?
    })
    .catch((error) => {
        console.log(error);
    });
```

**What is the output of the `Promise.all()` call here? How does `Promise.all()` behave when one of the promises rejects, and what will happen in that case?**

---

### **Question 4: Promise.allSettled() vs. Promise.all()**

```javascript
const promise1 = new Promise((resolve, reject) => {
    setTimeout(() => resolve('First'), 200);
});

const promise2 = new Promise((resolve, reject) => {
    setTimeout(() => reject('Second failed'), 100);
});

Promise.allSettled([promise1, promise2])
    .then((results) => {
        console.log(results);  // What will be logged?
    });
```

**What is the difference between `Promise.allSettled()` and `Promise.all()` in this case? What will happen when one of the promises rejects? How does `Promise.allSettled()` handle it differently from `Promise.all()`?**

---

### **Question 5: Promise.race()**

```javascript
const promise1 = new Promise((resolve, reject) => {
    setTimeout(() => resolve('First'), 300);
});

const promise2 = new Promise((resolve, reject) => {
    setTimeout(() => resolve('Second'), 200);
});

Promise.race([promise1, promise2])
    .then((result) => {
        console.log(result); // What will this log?
    });
```

**What is the behavior of `Promise.race()`? What will be the output in this case, and how does it differ from `Promise.all()`?**

---

### **Question 6: Promise.any()**

```javascript
const promise1 = new Promise((resolve, reject) => {
    setTimeout(() => reject('First failed'), 200);
});

const promise2 = new Promise((resolve, reject) => {
    setTimeout(() => resolve('Second'), 100);
});

Promise.any([promise1, promise2])
    .then((result) => {
        console.log(result); // What will this log?
    })
    .catch((error) => {
        console.log(error);
    });
```

**What will be the output of the `Promise.any()` call in this case? How does `Promise.any()` differ from `Promise.race()` and `Promise.all()`?**

---

### **Question 7: Async/Await with Try/Catch**

```javascript
async function fetchData() {
    const response = await new Promise((resolve, reject) => {
        setTimeout(() => reject("Error fetching data"), 1000);
    });
    return response;
}

async function run() {
    try {
        const data = await fetchData();
        console.log(data);
    } catch (error) {
        console.log(error);  // What will this log?
    }
}

run();
```

**How does `async/await` work with `try/catch` blocks? What happens when the promise inside the `await` call rejects? How does the `catch` block handle errors?**

---

### **Question 8: Chaining Promises with Async/Await**

```javascript
async function firstTask() {
    return new Promise((resolve) => {
        setTimeout(() => resolve("First task done"), 100);
    });
}

async function secondTask() {
    return new Promise((resolve) => {
        setTimeout(() => resolve("Second task done"), 200);
    });
}

async function runTasks() {
    const result1 = await firstTask();
    const result2 = await secondTask();
    return `${result1}, ${result2}`;
}

runTasks().then((result) => console.log(result));  // What will be logged?
```

**What is the order of execution in this async function? Can you optimize this code by running the tasks in parallel instead of sequentially?**

---

### **Question 9: Handling Multiple Errors in Promise Chains**

```javascript
const task1 = new Promise((resolve, reject) => {
    setTimeout(() => resolve('Task 1 completed'), 500);
});

const task2 = new Promise((resolve, reject) => {
    setTimeout(() => reject('Task 2 failed'), 200);
});

task1
    .then((result) => {
        console.log(result);  // What will this log?
        return task2;
    })
    .catch((error) => {
        console.log(error);  // What will this log?
        return 'Continuing after failure';
    })
    .finally(() => {
        console.log('This runs no matter what');
    });
```

**What will be the output of this promise chain? How does `.catch()` handle errors in the middle of a chain, and how does `.finally()` behave?**

---

### **Question 10: Await with Multiple Promises**

```javascript
async function fetchData1() {
    return new Promise((resolve) => {
        setTimeout(() => resolve("Data 1"), 200);
    });
}

async function fetchData2() {
    return new Promise((resolve) => {
        setTimeout(() => resolve("Data 2"), 100);
    });
}

async function fetchData3() {
    return new Promise((resolve) => {
        setTimeout(() => resolve("Data 3"), 50);
    });
}

async function run() {
    const data = await Promise.all([fetchData1(), fetchData2(), fetchData3()]);
    console.log(data);  // What will this log?
}

run();
```

**What will the output be here, and why? Can you optimize this code to make the promises run in parallel rather than sequentially? How does `Promise.all()` work with multiple promises like this?**

---

### **Question 11: Handling Multiple Errors in `Promise.allSettled()`**

```javascript
const promise1 = new Promise((resolve, reject) => {
    setTimeout(() => resolve("First"), 200);
});

const promise2 = new Promise((resolve, reject) => {
    setTimeout(() => reject("Second failed"), 100);
});

Promise.allSettled([promise1, promise2])
    .then((results) => {
        console.log(results);
    });
```

**What will be the output of `Promise.allSettled()` in this case? How does `Promise.allSettled()` behave when promises resolve and reject at different times?**

---

### **Question 12: Combining Async/Await with `Promise.all()`**

```javascript
async function task1() {
    return new Promise((resolve) => setTimeout(() => resolve('Task 1 done'), 300));
}

async function task2() {
    return new Promise((resolve) => setTimeout(() => resolve('Task 2 done'), 100));
}

async function run() {
    const results = await Promise.all([task1(), task2()]);
    console.log(results);  // What will be logged?
}

run();
```

**How does `Promise.all()` work in conjunction with `async/await` here? What happens if one of the promises rejects, and how can you handle this situation?**

---


### **Array Methods & Object Manipulation**

---

### **1. Iterate over an array using the `map()` function**
Given an array of numbers, use the `map()` function to multiply each element by 2 and return a new array.

```javascript
const numbers = [1, 2, 3, 4, 5];
// Your solution here
```

---

### **2. Filter out all the even numbers from an array**
Write a function that filters out all even numbers from the array and returns a new array of only odd numbers.

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];
// Your solution here
```

---

### **3. Use `reduce()` to sum up all elements in an array**
Given an array of numbers, use `reduce()` to calculate the sum of all the numbers in the array.

```javascript
const numbers = [1, 2, 3, 4, 5];
// Your solution here
```

---

### **4. Find the first number greater than a given value**
Use `find()` to find the first number greater than 5 in the array.

```javascript
const numbers = [1, 2, 3, 6, 7, 8];
// Your solution here
```

---

### **5. Flatten an array using `flat()`**
Given an array of nested arrays, use the `flat()` method to flatten the array into a single-level array.

```javascript
const nestedArray = [1, [2, 3], [4, [5, 6]]];
// Your solution here
```

---

### **6. Use `reduce()` to count occurrences of each element in an array**
Given an array of strings, use `reduce()` to count how many times each string appears in the array.

```javascript
const words = ['apple', 'banana', 'apple', 'orange', 'banana', 'banana'];
// Your solution here
```

---

### **7. Remove duplicates from an array using `Set`**
Use a `Set` to remove duplicates from an array of numbers.

```javascript
const numbers = [1, 2, 2, 3, 4, 4, 5];
// Your solution here
```

---

### **8. Merge two objects**
Write a function that merges two objects into one, without mutating the original objects.

```javascript
const obj1 = { name: 'John', age: 30 };
const obj2 = { job: 'Developer', city: 'New York' };
// Your solution here
```

---

### **9. Use `Object.keys()` to extract keys from an object**
Write a function that returns the keys of an object as an array.

```javascript
const person = { name: 'Alice', age: 25, city: 'Paris' };
// Your solution here
```

---

### **10. Deep copy an object using `JSON.parse()` and `JSON.stringify()`**
Write a function to deep clone an object using `JSON.parse()` and `JSON.stringify()`.

```javascript
const obj = { a: 1, b: { c: 2 } };
// Your solution here
```

---

### **Async/Await & Promises**

---

### **11. Fetch data using `async/await` and handle errors**
Write a function using `async/await` to fetch data from an API and handle any errors that might occur during the fetch operation.

```javascript
async function fetchData(url) {
  // Your solution here
}
```

---

### **12. Implement a custom `debounce` function**
Write a function `debounce()` that delays the execution of a given function by a specified amount of time.

```javascript
function debounce(fn, delay) {
  // Your solution here
}
```

---

### **13. Implement a custom `throttle` function**
Write a function `throttle()` that ensures a given function is only called once in a specified time interval.

```javascript
function throttle(fn, delay) {
  // Your solution here
}
```

---

### **14. Chain multiple promises using `.then()`**
Create a series of promises that execute in sequence. The first promise resolves to "Step 1", the second promise resolves to "Step 2", and so on.

```javascript
function step1() {
  return new Promise(resolve => resolve("Step 1"));
}

function step2() {
  return new Promise(resolve => resolve("Step 2"));
}

step1()
  .then(result => {
    console.log(result); // "Step 1"
    return step2();
  })
  .then(result => console.log(result)); // "Step 2"
```

---

### **15. Use `Promise.all()` to execute multiple asynchronous operations**
Given an array of promises, use `Promise.all()` to execute all promises and log their results.

```javascript
const promise1 = new Promise(resolve => setTimeout(() => resolve('Result 1'), 1000));
const promise2 = new Promise(resolve => setTimeout(() => resolve('Result 2'), 2000));

Promise.all([promise1, promise2]).then(results => {
  console.log(results); // What will be logged?
});
```

---

### **16. Handle errors with `Promise.all()`**
Handle a scenario where one of the promises in `Promise.all()` fails by catching the error.

```javascript
const promise1 = new Promise(resolve => setTimeout(() => resolve('Result 1'), 1000));
const promise2 = new Promise((resolve, reject) => setTimeout(() => reject('Error'), 2000));

Promise.all([promise1, promise2])
  .then(results => console.log(results))
  .catch(error => console.log(error)); // What will be logged?
```

---

### **17. Use `Promise.race()` to get the first resolved promise**
Write a function that returns the first resolved promise out of multiple promises using `Promise.race()`.

```javascript
const promise1 = new Promise(resolve => setTimeout(() => resolve('First'), 200));
const promise2 = new Promise(resolve => setTimeout(() => resolve('Second'), 100));

Promise.race([promise1, promise2]).then(result => {
  console.log(result); // What will this log?
});
```

---

### **18. Use `Promise.any()` to get the first resolved promise (ignoring rejected ones)**
Write a function using `Promise.any()` to get the first successfully resolved promise.

```javascript
const promise1 = new Promise((resolve, reject) => setTimeout(() => reject('Error 1'), 200));
const promise2 = new Promise(resolve => setTimeout(() => resolve('Success'), 100));

Promise.any([promise1, promise2]).then(result => {
  console.log(result); // What will this log?
});
```

---

### **19. Create a `customPromise` function**
Write a custom implementation of a promise that resolves after 1 second with a message.

```javascript
function customPromise() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Custom promise resolved!");
    }, 1000);
  });
}

customPromise().then(result => console.log(result)); // What will this log?
```

---

### **20. Use `async/await` with `Promise.all()`**
Write an `async` function that waits for multiple promises to resolve using `Promise.all()` and then logs the results.

```javascript
async function run() {
  const promise1 = new Promise(resolve => setTimeout(() => resolve("Data 1"), 500));
  const promise2 = new Promise(resolve => setTimeout(() => resolve("Data 2"), 1000));

  const results = await Promise.all([promise1, promise2]);
  console.log(results); // What will be logged?
}
```

---

### **21. Use `finally()` in promise chaining**
Write a function that always runs some cleanup code using `.finally()` after promise resolution or rejection.

```javascript
const task = new Promise((resolve, reject) => {
  setTimeout(() => resolve('Task Complete'), 1000);
});

task
  .then(result => console.log(result))
  .catch(error => console.log(error))
  .finally(() => console.log('Cleanup completed'));
```

---

### **Difficult Questions on `map()`, `filter()`, and `reduce()`**

---

### **1. Transform an array of objects using `map()`**

Given an array of objects representing employees, use `map()` to transform the data into an array of strings where each string contains the employee's name and their department.

```javascript
const employees = [
    { id: 1, name: 'Alice', department: 'HR' },
    { id: 2, name: 'Bob', department: 'Engineering' },
    { id: 3, name: 'Charlie', department: 'Sales' }
];

// Expected Output:
// ["Alice from HR", "Bob from Engineering", "Charlie from Sales"]
```

---

### **2. Filter out items from an array based on a condition**

Given an array of objects representing books, use `filter()` to create a new array with books that have a rating of 4 or higher.

```javascript
const books = [
    { title: 'Book 1', rating: 4.2 },
    { title: 'Book 2', rating: 3.8 },
    { title: 'Book 3', rating: 5.0 },
    { title: 'Book 4', rating: 2.5 }
];

// Expected Output:
// [{ title: 'Book 1', rating: 4.2 }, { title: 'Book 3', rating: 5.0 }]
```

---

### **3. Combine `map()` and `filter()` to process an array of objects**

You have an array of products, each product has a `price` and `category`. Use `map()` to increase the price of all products by 10%, and then use `filter()` to return only those products in the `Electronics` category.

```javascript
const products = [
    { id: 1, name: 'Laptop', category: 'Electronics', price: 1000 },
    { id: 2, name: 'Shirt', category: 'Clothing', price: 30 },
    { id: 3, name: 'Headphones', category: 'Electronics', price: 200 },
    { id: 4, name: 'Book', category: 'Education', price: 15 }
];

// Expected Output:
// [{ id: 1, name: 'Laptop', category: 'Electronics', price: 1100 },
//  { id: 3, name: 'Headphones', category: 'Electronics', price: 220 }]
```

---

### **4. Use `reduce()` to count frequency of elements in an array**

Given an array of strings, use `reduce()` to count how many times each word appears in the array. Return an object where the keys are the words, and the values are their frequency count.

```javascript
const words = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple'];

// Expected Output:
// { apple: 3, banana: 2, orange: 1 }
```

---

### **5. Implement a `flatten()` function using `reduce()`**

Given a nested array, use `reduce()` to flatten the array into a single-level array.

```javascript
const nestedArray = [1, [2, 3], [4, [5, 6]]];

// Expected Output:
// [1, 2, 3, 4, 5, 6]
```

---

### **6. Use `map()` to create an array of nested objects**

Given an array of numbers, use `map()` to create a new array of objects where each object contains the number and its square.

```javascript
const numbers = [1, 2, 3, 4, 5];

// Expected Output:
// [{ number: 1, square: 1 }, { number: 2, square: 4 }, { number: 3, square: 9 }, { number: 4, square: 16 }, { number: 5, square: 25 }]
```

---

### **7. Use `reduce()` to group objects by a property**

You have an array of objects representing people, each person has a `name` and `age`. Use `reduce()` to group the people by their age.

```javascript
const people = [
    { name: 'Alice', age: 25 },
    { name: 'Bob', age: 30 },
    { name: 'Charlie', age: 25 },
    { name: 'David', age: 30 }
];

// Expected Output:
// {
//   25: [{ name: 'Alice', age: 25 }, { name: 'Charlie', age: 25 }],
//   30: [{ name: 'Bob', age: 30 }, { name: 'David', age: 30 }]
// }
```

---

### **8. Combine `map()` and `reduce()` to transform and accumulate data**

Given an array of objects where each object represents a product, use `map()` to apply a 15% discount to each product's price, and then use `reduce()` to calculate the total price of all products after the discount.

```javascript
const products = [
    { id: 1, name: 'Laptop', price: 1000 },
    { id: 2, name: 'Phone', price: 500 },
    { id: 3, name: 'Tablet', price: 300 }
];

// Expected Output:
// Total price after discount: 1680
```

---

### **9. Use `map()` and `filter()` to manipulate an array of mixed data types**

Given an array that contains both numbers and strings, use `map()` to convert all numbers to strings, and then use `filter()` to keep only the items that are not equal to "0".

```javascript
const mixedData = [1, '2', 3, '0', '5', 0];

// Expected Output:
// ['1', '2', '3', '5']
```

---

### **10. Use `reduce()` to create a cumulative sum of an array**

Given an array of numbers, use `reduce()` to calculate the cumulative sum of the array. The output should be an array where each element is the sum of all elements up to that index.

```javascript
const numbers = [1, 2, 3, 4, 5];

// Expected Output:
// [1, 3, 6, 10, 15]
```

---

### **11. Use `map()` and `filter()` to transform and remove objects**

Given an array of objects representing students, each object has `name`, `score`, and `passed` (boolean). Use `map()` to increase the score by 5 points for all students who passed, and then use `filter()` to only keep students with scores above 50.

```javascript
const students = [
    { name: 'Alice', score: 45, passed: false },
    { name: 'Bob', score: 55, passed: true },
    { name: 'Charlie', score: 65, passed: true },
    { name: 'David', score: 50, passed: true }
];

// Expected Output:
// [{ name: 'Bob', score: 60, passed: true }, { name: 'Charlie', score: 70, passed: true }, { name: 'David', score: 55, passed: true }]
```

---

### **12. Create a `deepClone()` function using `reduce()`**

Write a function that deep clones an object using `reduce()` to iterate over the object's keys and values. The function should handle nested objects as well.

```javascript
const originalObj = {
    a: 1,
    b: {
        c: 2,
        d: 3
    },
    e: 4
};

// Expected Output:
// { a: 1, b: { c: 2, d: 3 }, e: 4 }
```

---

### **13. Use `map()` to calculate the sum of all numbers in an array of objects**

Given an array of objects representing different users and their expenses, use `map()` to calculate the total sum of all expenses.

```javascript
const expenses = [
    { user: 'Alice', amount: 100 },
    { user: 'Bob', amount: 200 },
    { user: 'Charlie', amount: 50 }
];

// Expected Output:
// 350
```

---

### **14. Group an array of objects by a dynamic key using `reduce()`**

Given an array of objects representing products, each product has a `category` and `price`. Use `reduce()` to group the products by their `category` and calculate the total price for each category.

```javascript
const products = [
    { name: 'Shampoo', category: 'Health', price: 5 },
    { name: 'Toothpaste', category: 'Health', price: 3 },
    { name: 'Laptop', category: 'Electronics', price: 1000 },
    { name: 'Phone', category: 'Electronics', price: 500 }
];

// Expected Output:
// {
//   Health: { total: 8, products: [{ name: 'Shampoo', price: 5 }, { name: 'Toothpaste', price: 3 }] },
//   Electronics: { total: 1500, products: [{ name: 'Laptop', price: 1000 }, { name: 'Phone', price: 500 }] }
// }
```

---

### **15. Use `map()` and `reduce()` to find the highest priced product in each category**

Given an array of products, where each product has a `category` and a `price`, use `map()` to extract the prices for each category, and then use `reduce()` to find the highest priced product in each category.

```javascript
const products = [
    { name: 'Shampoo', category: 'Health', price: 5 },
    { name: 'Toothpaste', category: 'Health', price: 3 },
    { name: 'Laptop', category: 'Electronics', price: 1000 },
    { name: 'Phone', category: 'Electronics', price: 500 },
    { name: 'TV', category: 'Electronics', price: 1200 }
];

// Expected Output:
// { Health: 5, Electronics: 1200 }
```

---
