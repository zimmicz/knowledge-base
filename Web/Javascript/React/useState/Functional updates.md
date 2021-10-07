# Functional updates

``` javascript
const useToggle = () => {
	const [on, setOn] = React.useState(false);
	
	const toggle = () => setOn(!on);
	
	return [on, toggle];
}
```

Although this looks ok