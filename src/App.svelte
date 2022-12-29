<script>
	import Header from './UI/Header.svelte';
	import MeetupGrid from './Meetups/MeetupGrid.svelte';
	import Textinput from './UI/Textinput.svelte';
	import Button from './UI/Button.svelte';
	import EditMeetup from './Meetups/EditMeetup.svelte';

	let meetups = [
		{
			id: 'm1',
			title: 'Coding Bootcamp',
			subtitle: 'Learn to code in 2 hours',
			description: 'In this meetup, we will have experts that teach you how to code!',
			imageUrl:
				'https://cdn.pixabay.com/photo/2014/11/21/18/25/christmas-market-540918_960_720.jpg',
			address: '27th Nerd Road, 32523 New York',
			email: 'blahblah@example.com',
			isFavorite: false
		},
		{
			id: 'm2',
			title: 'Swimming',
			subtitle: 'Learn to swim in 2 hours',
			description: 'In this meetup, we will have experts that teach you how to swim!',
			imageUrl: 'https://cdn.pixabay.com/photo/2022/12/02/20/09/icicle-7631570_960_720.jpg',
			address: '27th Nerd Road, 32523 New York',
			email: 'aaa@example.com',
			isFavorite: false
		}
	];

	let editMode;

	function cancelEdit() {
		editMode = null;
	}

	function addMeetup(event) {
		const newMeetup = {
			id: Math.random().toString(),
			title: event.detail.title,
			subtitle: event.detail.subtitle,
			address: event.detail.address,
			email: event.detail.email,
			description: event.detail.description,
			imageUrl: event.detail.imageUrl
		};
		meetups = [newMeetup, ...meetups];
		editMode = null;
	}

	function toggleFavorite(event) {
		const id = event.detail;
		const updatedMeetup = { ...meetups.find((m) => m.id === id) };
		updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
		const meetupIndex = meetups.findIndex((m) => m.id === id);
		const updatedMeetups = [...meetups];
		updatedMeetups[meetupIndex] = updatedMeetup;
		meetups = updatedMeetups;
	}
</script>

<Header />
<main>
	<div class="meetup-controls">
		<Button on:click={() => (editMode = 'add')}>New Meetup</Button>
		{#if editMode === 'add'}
			<EditMeetup on:save={addMeetup} on:cancel={cancelEdit} />
		{/if}
		<MeetupGrid {meetups} , on:togglefavorite={toggleFavorite} />
	</div>
</main>

<style>
	main {
		margin-top: 5rem;
	}

	.meetup-controls {
		margin: 1rem;
	}
</style>
