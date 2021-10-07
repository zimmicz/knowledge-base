# Functional updates

``` javascript
const useToggle = () => {
	const [on, setOn] = React.useState(false);
	
	const toggle = () => setToggle(!on);
	
	return [on, toggle];
}
```

Although this looks ok