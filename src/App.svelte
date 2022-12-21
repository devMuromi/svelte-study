<script>
	import Header from './UI/Header.svelte';
	import MeetupItem from './Meetups/MeetupItem.svelte';

	const meetups = [
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
</script>

<Header />

<section id="meetups">
	{#each meetups as meetup}
		<MeetupItem {meetup} />
	{/each}
</section>

<style>
	#meetups {
		margin-top: 5rem;
	}
</style>
