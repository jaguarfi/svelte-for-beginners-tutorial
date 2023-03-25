<script>
	export let name;
	let beltColour = 'black';

	const updateBeltColour = () => {
		beltColour = 'red';
	};
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Hello, Ninja with {beltColour} belt</p>
	<button on:click={updateBeltColour}>update belt color</button>
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