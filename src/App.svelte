<script>
	import ContactCard from './ContactCard.svelte';

	let name = 'Muromi';
	let age = 21;
	let title = "here come's title";
	let description = 'A simple description';
	let imageURL = 'https://randomuser.me/api/portraits';

	$: uppercaseName = name.toUpperCase();

	$: if (name == 'rika') {
		age = 1;
	}

	function incrementAge() {
		age += 1;
	}

	//   function changeName() {
	//     name = "rika";
	//   }

	//   function nameInput(e) {
	//     name = e.target.value;
	//   }
</script>

<main>
	<h1>Hello {uppercaseName}!, my age is {age}</h1>
	<button on:click={incrementAge}>Change Age</button>
	<!-- <button on:click={changeName}>Change Name</button> -->
	<input type="text" bind:value={name} />
	<input type="text" bind:value={title} />
	<textarea rows="3" bind:value={description} />
	<input type="text" bind:value={imageURL} />

	<ContactCard userName={name} jobTitle={title} {description} {imageURL} />
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
