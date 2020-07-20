# Javascript

[Generators](https://www.notion.so/Generators-a47f6016b41e4bc4afaf05d9a2815c25) 

**ECMAScript**: Specification that javascript implements

**Javascript Interpreter:** reads and executes javascript code common examples are web browsers and Node.js

- Each interpreter supports a different version of ES (ECMAScript)

**Transpilers:** converts a version of ES to a different version.

- Typically used when you want to use a newer version of ES on an interpreter that doesn't support it
- Babel to convert new versions of JS for the browser who are slower to support versions of ES
- Also converts JSX (react) to normal javascript so it can be run on the browser

**Versions:** 

- **ES5 (2009):** widely supported version of ES (many essential features).
- **ES6 (2015):** Modules, classes, promises, template literals, destructuring, generators, Map and set structures
- **ES7 (2016):** Exponential operator, Array.includes
- **ES8 (2017):** Async / Await, Object entries, String padding
    - Object.entries: returns an array of key values pairs that you can iterator over
- **ES9 (2018):** Async iteration, Promise.finally, Rest / spread, Regex improvements
    - Async iteration: for await (let var of iteravble) { statement }
- **ES10 (2019):** array.flat(): flattens nested arrays into a single flat array, string.trim()

**Browser Support:** 

- All browsers support ES6 as of early 2017
- Only chrome and opera support ES7 as of mid 2020

**Call Stack:**

- Stack of execution contexts
- Executed in a last in first out order
- Primitive data is stored here
- This is where closures take place
- FIFO

**Heap Memory:**

- Where objects are stored
- Orphaned objects (ones that no longer have a function referencing them) are clean up periodically by the garbage collector
    - GC in javascript uses the mark and sweep algorithm
    - Global variables, event listeners and setIntervals need to be cleared manually
- Primitive data is store in the call stack

The Event Queue: A queue of functions to be executed because of events that have occured.

The Event Table: Keeps track of what functions are waiting on what events.

DOM: Document object model

- Tree structure of elements that make up a page, generated from the html you write.
- Can be manipulated by javascript using the DOM api
- The dom is slow to update hence the use of virtual DOMS like in react.
- Visible in the developer console

Virtual DOM:

- Representation of the DOM kept in memory and syncs with the actual DOM periodically
- Written in javascript
- Significantly faster to update compared to the DOM
- Update Process:
    1. Some state change takes place
    2. React creates a new VDOM to represent the new state
    3. React compares the new VDOM to the old for changes
    4. Rerenders the changes in the dom, only making the necessary changes not re-rendering the whole dom