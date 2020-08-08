# React Reference

### Class Lifecycle:

![https://i2.wp.com/programmingwithmosh.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-31-at-1.44.28-PM.png?ssl=1](https://i2.wp.com/programmingwithmosh.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-31-at-1.44.28-PM.png?ssl=1)

# Hooks

React Hooks allows Function components to “hook” into the React state and lifecycle. Let’s look at an example.

## UseState:

---

Returns a stateful value, and a function to update it.

```jsx
const [state, setState] = useState(initialState);
```

Functional updates:

Pass a function to derive new state from previous state

```jsx
function Counter({initialCount}) {
  const [count, setCount] = useState(initialCount);
  return (<button onClick={() => setCount(prevCount => prevCount + 1)}>+</button>);
}
```

## UseEffect:

---

Adds an function (an effect) to use after a render

you can think of useEffect Hook as componentDidMount, componentDidUpdate, and componentWillUnmount combined.

By default, it runs both after the first render and after every update

### Default Example

```jsx
//default example
useEffect(() => {
    document.title = `You clicked ${count} times`;
  });
```

### With Clean up:

Return a function to be run on unmount (for cleanup)

```jsx
//cleanup example
useEffect(() => {
  document.title = `You clicked ${count} times`;
	return function cleanup() {
    ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
  };
});
```

## Only on value update:

```jsx
useEffect(() => {
  setIsOnline(status.isOnline);
}, [props.friend.id]);
```

## Only on the first Render:

```jsx
useEffect(() => {
  setIsOnline(status.isOnline);
}, []);
```

## UseContext:

---

3 parts:

Create the context:

```jsx
const ThemeContext = React.createContext('test');
```

Wrap with the provider:

```jsx
import React, {useState} from 'react';
import ThemeContext from './themeContext.js';

function App() {
const [textValue, setTextValue] = useState('test');
  return (
    <ThemeContext.Provider value={{textValue, setTextValue}}>
      <Toolbar />
    </ThemeContext.Provider>
	);
}
```

Use in the child component:

```jsx
**import ThemeContext from './themeContext.js';

function Toolbar () {
  const {textValue, setTextValue} = useContext(ThemeContext);
  return (
    <button onClick={() => {setTextValue('new Text')}>
			{**textValue**}
		</button>
  );
}**
```

## UseReducer:

---

Enhanced version of use state following the paradigme set by reducers in Redux

```jsx
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

## UseMemo:

---

prevents a function from re-running if a given input does not change (same as in recursive algorithms)

## UseCallback:

---

useCallback(fn, deps) is equivalent to useMemo(() => fn, deps).

this way the function can be defined in the functional component (wherein useMemo it should be a pure function and moved outside)

- React performance testing: Flame graph
    - devtools ⇒ profiler

- Portals:
    - allows you to render react components into a dom node that exists outside of the DOM hierarchy of the parent component. ie. the root

- Context api:
    - provides a way to pass data through the component tree without having to pass props down manually at every level
    - designed to be used for "global" state data not localized state.