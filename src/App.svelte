<script>
	import Header from './UI/Header.svelte';

	import MeetupGrid from './Meetups/MeetupGrid.svelte';

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
		<div class="form-control">
			<label for="title">Title</label>
			<input type="text" id="title" bind:value={title} />
		</div>
		<div class="form-control">
			<label for="subtitle">Subtitle</label>
			<input type="text" id="subtitle" bind:value={subtitle} />
		</div>
		<div class="form-control">
			<label for="address">Address</label>
			<input type="text" id="address" bind:value={address} />
		</div>
		<div class="form-control">
			<label for="imageUrl">Image URL</label>
			<input type="text" id="imageUrl" bind:value={imageUrl} />
		</div>
		<div class="form-control">
			<label for="email">E-Mail</label>
			<input type="email" id="email" bind:value={email} />
		</div>
		<div class="form-control">
			<label for="description">Description</label>
			<textarea rows="3" id="description" bind:value={description} />
		</div>
		<button type="submit">Save</button>
	</form>
	<MeetupGrid {meetups} />
</main>

<style>
	main {
		margin-top: 5rem;
	}
</style>
