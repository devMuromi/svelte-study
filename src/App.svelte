<script>
  let name = "muromi";
  let age = 21;

  $: uppercaseName = name.toUpperCase();

  $: if (name == "rika") {
    age = 1;
  }

  function incrementAge() {
    age += 1;
  }

  function changeName() {
    name = "rika";
  }
</script>

<main>
  <h1>Hello {uppercaseName}!, my age is {age}</h1>
  <button on:click={incrementAge}>Change Age</button>
  <button on:click={changeName}>Change Name</button>

  <p>
    Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
    how to build Svelte apps.
  </p>
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
