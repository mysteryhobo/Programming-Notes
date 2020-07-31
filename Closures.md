# Closures

When a javascript execution context has access to variables of another execution context whether or not that execution context continues to exist

### Data Privacy

Closures can be used to create privacy like in the following example

```jsx
const getSecret = (secret) => {
  return {
    get: () => secret
  };
};
```

The only way to access the secret from the returned object is the .get() function

The following does not work

```jsx
object.secret = 'somethingNew'; // Does not work
```

### Stateful Functions / Dependency Injection

Closures can also be use to create stateful functions

```jsx
const createAdder = (value1) {
	return (value2) => value1 + value2
}

const add10 = createAdder(10);
console.log(add10(3)) // 13
```

You can also use this functionality to inject dependencies:

```jsx
const createRepository = (databaseORM, logger, errorHandler, ect..) => ({
	createUser: () => {},
	deleteUser: () => {},
	updateUser: () => {} 
})
```

Now the repository has access to dependencies while being abstracted away from their initialization and implementation.

You can initialize the logger in the server and pass it into the creation of the repo.

For example, this is really useful if you wanted to switch from Morgan to Winston as a logging library.

You can also use closures to essentially save the state of a changing variable.

```jsx
// The following code outputs: 5 5 5 5 5
for (var i = 0; i < 5; i++) {
  setTimeout(() => console.log(i), 1000);
}

// This outputs 1 2 3 4 5
for (var i = 0; i < 5; i++) {
  ((j) => {
    setTimeout(() => console.log(j), 1000);
  })(i)
}
```

The second implementation creates a closures around the variable "i" at the moment when the inner function is defined, thus maintaining its current value when the inner function is executed on the next tick.