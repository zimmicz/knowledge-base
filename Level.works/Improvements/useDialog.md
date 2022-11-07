## Requirements
- reusable
- sane defaults easy to use
- possible to pass JSX to the component
- gives you both the component and its props back

``` javascript
const MyComponent = () => {
	
	const dialog = Dialog.useDialog();
	const prompt = Dialog.useDialog();
	
	return (
	<>
	<button onClick={() => dialog.open()}
	
	<Dialog open={dialog.isOpen} onClose={dialog.close}>
		<Dialog.Title>Title</Dialog.Title>
		<Dialog.Content>Content</Dialog.Content>
		<Dialog.Actions
			confirm={<Dialog.Button onClick={() => {dialog.close()}}>ok</Dialog.Button>}
			cancel={<Dialog.Button onClick={() => { dialog.close()}}>cancel</Dialog.Button>}
		/>
	</Dialog>
	
	<Prompt open={prompt.isOpen} onClose={prompt.close}>
		<Prompt.Title>Title</Prompt.Title>
		<Prompt.Content>lorem ipsum dolor sit amet</Prompt.Content>
		<Prompt.Confirm>ok</Prompt.Confirm>
		<Prompt.Cancel>cancel</Prompt.Cancel>
	</Prompt>

	<Not
	</>)
}
```

``` js
const Prompt = (props) => {
  const dialog = Dialog.useDialog();

	return (
		<Dialog {...props}>
			<Dialog.Title>Confirm me</Dialog.Title>
			<Dialog.Content>Content</Dialog.Content>
		</Dialog>
	)
}
```