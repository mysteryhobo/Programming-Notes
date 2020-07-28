# This

### Function declarations:

- 'This' is based on where the function is invoked.
- If the function is invoked on an object the 'this' will be the object
- If the function is NOT invoked on any object it will
    - default to the global object if in strict mode
    - default to undefined if in strict mode

```jsx
"use strict";

const obj = {
	testFunc: function () {
  	console.log('this:',this);
  }
}

obj.testFunc(); // outputs: obj because it is executed on the object

const testVar = obj.testFunc
testVar(); //outputs: undefined or global object (if not in strict mode)
```

1. Method
    - The function is a method and is executed on the object so it uses the object as its execution context.
2. method removed from the object and executed
    - the function is no longer executed as a method so it uses the global (or undefined in strict mode) as its execution context.

### F**unction expressions: (Fat Arrow)**

- 'This' is based on where the function is defined. (its lexical scope)
- it inherits its parents scope
- NOTE: You can create a function expression with the normal (non-fat arrow) syntax. This convention just follows the traditional function definition rules for execution contexts. ie. it does not inherit from the parent

```jsx
this.test = 'test';
const outerTest = () => {console.log('this:', this);}
const obj = {
  test: () => {console.log('this;', this)},
  test2: function () { return () => {console.log('this:', this)} }
};

outerTest(); // See #1 in Notes
obj.test(); // See #2 in Notes
obj.test2()(); // See #3 in Notes
const testFunc = obj.test2
testFunc()(); // See #4 in Notes
```

1. A function expression defined in the file scope
    - If in node 'this' is equal to the module's execution context
    - If in the console 'this' is the Window object
2. A function expression defined in an object
    - function expressions in an object does not inherit the object as the execution context, so 'this' is still the global (or module) object
3. A function expression defined inside a method
    - The function expression inherits the execution context of the containing function which in this case is the obj since the function is a method. so, the 'this' is the obj
4. A function expression defined in a function definition
    - the function expression inherits the execution context of the containing function which in this case is the global object or undefined if in strict mode since it is no longer referenced as a method.

**function.bind(this):** Sets the this of the function

**function.call(this, param1, param2):** Calls the function with a provided execution context

**function.apply(this, [param1, param2]):** Does the same as call but you pass parameters as an array

## React:

In React we use .bind(this) to explicitly attach the execution context of the component to a function because otherwise the execution context of the function would be undefined and you would not be able to set the state.