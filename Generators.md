# Generators

Pausable functions.

Use the * notation after 'function' to turn it into a generator.

Use the yield keyword in the function to pause it with some output

Pass in values to replace the yield with generator.next(value)

```jsx
let createGenerator = function*() {
	let myVar1 = yield 1;

	console.log(myVar1) //outputs 'Test Value'
}

let myGenerator = createGenerator(); //creates / gets the generator ready to run

testVal = myGenerator.next('Test Value') // returns 1, sets the yield equal to 'Test Value'

console.log(testVal) //outputs 1
```