<script>
	import { createEventDispatcher } from 'svelte';
	import Textinput from '../UI/Textinput.svelte';
	import Button from '../UI/Button.svelte';
	import Modal from '../UI/Modal.svelte';

	let title = '';
	let subtitle = '';
	let address = '';
	let email = '';
	let description = '';
	let imageUrl = '';

	const dispatch = createEventDispatcher();

	function submitForm() {
		dispatch('save', {
			title: title,
			subtitle: subtitle,
			address: address,
			email: email,
			description: description,
			imageUrl: imageUrl
		});
	}
	function cancel() {
		dispatch('cancel');
	}
</script>

<Modal title="Edit Meetup Data" on:cancel>
	<form on:submit|preventDefault={submitForm}>
		<Textinput
			id="title"
			label="Title"
			value={title}
			on:input={(event) => (title = event.target.value)}
		/>
		<Textinput
			id="title"
			label="Subtitle"
			value={subtitle}
			on:input={(event) => (subtitle = event.target.value)}
		/>
		<Textinput
			id="address"
			label="Address"
			value={address}
			on:input={(event) => (address = event.target.value)}
		/>
		<Textinput
			id="imageUrl"
			label="Image URL"
			value={imageUrl}
			on:input={(event) => (imageUrl = event.target.value)}
		/>
		<Textinput
			id="email"
			label="E-Mail"
			value={email}
			type="email"
			on:input={(event) => (email = event.target.value)}
		/>
		<Textinput
			id="description"
			label="Description"
			value={description}
			controlType="textarea"
			on:input={(event) => (description = event.target.value)}
		/>
	</form>
	<div slot="footer">
		<Button type="button" mode="outline" on:click={cancel}>Cancel</Button>
		<Button type="button" on:click={submitForm}>Save</Button>
	</div>
</Modal>

<style>
	form {
		width: 100%;
	}
</style>
