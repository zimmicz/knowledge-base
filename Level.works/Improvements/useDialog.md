## Requirements
- reusable
- sane defaults easy to use
- possible to pass JSX to the component
- gives you both the component and its props back

``` javascript
const MyComponent = () => {
	
	const dialog = Dialog.useDialog();
	const prompt = Dialog.useDialog();
	const notify = Dialog.useDialog();
	
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

	<Notify open={notify.isOpen} onClose={notify.close}>Hello world</Notify>
	</>)
}
```

``` js
const Prompt = (props) => {
  const dialog = Dialog.useDialog();

	return (
		<Dialog {...props}>
			{children}
		</Dialog>
	)
}

const Notify = () => {
	return (
		<Dialog {...props}>
		{children}
		<Dialog.Actions>
			<Button>close</Button>
		</Dialog.Actions>
		</Dialog>
	)
}
```