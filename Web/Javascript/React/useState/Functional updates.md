# Functional updates

``` javascript
const useToggle = () => {
	const [on, setOn] = React.useState(false);
	
	const toggle = () => setOn(!on);
	
	return [on, toggle];
}
```

Although this looks ok, it hides a lot of trouble. `toggle` function is different on every render. `useCallback` might sort this issue out:
```javascript
	const useToggle = () => {
	const [on, setOn] = React.useState(false);
	
	const toggle = React.useCallback(
		() => setOn(!on),
		[on]
	);
	
	return [on, toggle];
}
```

**However, this will not work**, because `on` change effectively changes the result of `useCallback`, and that leads to infinite loop.

Using functional update completely removes the dependency on `on` value. **This will work just fine**, because the `useCallback` stays the same.

```javascript
	const useToggle = () => {
	const [on, setOn] = React.useState(false);
	
	const toggle = React.useCallback(
		() => setOn(v => !v),
		[]
	);
	
	return [on, toggle];
}
```

Run this code to see it break.

```jsx
import React from "react";
  
const useToggle = () => {
	const [on, setOn] = React.useState(false);
	const toggle = React.useCallback(() => setOn(!on), [on]); 

	return [on, toggle];
};
  
export default function App() {
	const [on, toggleOn] = useToggle();
	const [count, setCount] = React.useState(0);

	React.useEffect(() => {
		if (!count) {
			return;
		}
		toggleOn();
	}, [count, toggleOn]);

	return (
		<div className="App">
			<h1>Hello CodeSandbox</h1>
			<h2>Start editing to see some magic happen!</h2>
			{on ? "on" : "off"}
			{count}
			<button onClick={toggleOn}>toggle</button>
			<button onClick={() => setCount((cnt) => cnt + 1)}>increment</button>
		</div>
	);
}
```