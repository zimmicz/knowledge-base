## Requirements
- reusable
- sane defaults easy to use
- possible to pass JSX to the component
- gives you both the component and its props back

``` javascript
const MyComponent = () => {
	
	const dialog = Dialog.useDialog();
	
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
	<ConfirmationDialog>
		<ConfirmationDialog.Title>Title</ConfirmationDialog.Title>
		<ConfirmationDialog.Content>lorem ipsum dolor sit amet</ConfirmationDialog.Content>
	</ConfirmationDialog>
	</>)
}
```

``` js
const ConfirmationDialog = (props) => {
  const dialog = Dialog.useDialog();

	return (
		<Dialog {...props}>
			<Dialog.Title>Confirm me</Dialog.Title>
			<Dialog.Content>Content</Dialog.Content>
		</Dialog>
	)
}
```