<script>
	export let firstName = 'John';
	export let lastName = 'Doe';
	let beltColour = 'black';

	$: name = `${firstName} ${lastName}`;
	$: {
		console.log(name);
		console.log(beltColour);
	}

</script>

<main>
	<h1>Hello {name}!</h1>
	<p style="color: {beltColour}">You are a Ninja with {beltColour} belt</p> 
	<input type="text" bind:value={firstName}>
	<input type="text" bind:value={lastName}>
	<input type="text" bind:value={beltColour}>
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