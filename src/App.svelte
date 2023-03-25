<script>
	export let name;
	let beltColour = 'black';

	const updateBeltColour = () => {
		beltColour = 'red';
	};

	// I could have used this function and call it from the main by adding the following line of code
	// <input on:input={handleInput} type="text" value={beltColour}>. However, using bind:value is a shorter way of 
	// doing the same thing.
	// const handleInput = (e) => {
	// 	beltColour = e.target.value;
	// };
</script>

<main>
	<h1>Hello {name}!</h1>
	<p style="color: {beltColour}">Hello, Ninja with {beltColour} belt</p>
	<button on:click={updateBeltColour}>update belt color</button>
	<!-- <input on:input={handleInput} type="text" value={beltColour}> -->
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