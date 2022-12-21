<script>
	import Header from './UI/Header.svelte';
	import MeetupGrid from './Meetups/MeetupGrid.svelte';
	import Textinput from './UI/Textinput.svelte';
	import Button from './UI/Button.svelte';

	let title = '';
	let subtitle = '';
	let address = '';
	let email = '';
	let description = '';
	let imageUrl = '';

	let meetups = [
		{
			id: 'm1',
			title: 'Coding Bootcamp',
			subtitle: 'Learn to code in 2 hours',
			description: 'In this meetup, we will have experts that teach you how to code!',
			imageUrl:
				'https://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/Codecademy_logo.svg/1200px-Codecademy_logo.svg.png',
			address: '27th Nerd Road, 32523 New York',
			email: 'blahblah@example.com'
		},
		{
			id: 'm2',
			title: 'Swimming',
			subtitle: 'Learn to swim in 2 hours',
			description: 'In this meetup, we will have experts that teach you how to swim!',
			imageUrl:
				'https://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/Codecademy_logo.svg/1200px-Codecademy_logo.svg.png',
			address: '27th Nerd Road, 32523 New York',
			email: 'aaa@example.com'
		}
	];

	function addMeetup() {
		const newMeetup = {
			id: Math.random().toString(),
			title: title,
			subtitle: subtitle,
			address: address,
			email: email,
			description: description,
			imageUrl: imageUrl
		};
		meetups = [newMeetup, ...meetups];
	}
</script>

<Header />
<main>
	<form on:submit|preventDefault={addMeetup}>
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
		<Button type="submit" caption="Save" />
	</form>
	<MeetupGrid {meetups} />
</main>

<style>
	main {
		margin-top: 5rem;
	}

	form {
		width: 30rem;
		max-width: 90%;
		margin: auto;
	}
</style>
