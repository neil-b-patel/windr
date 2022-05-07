<script>
	import Grid from './Grid.svelte'
	import YarnForm from './YarnForm.svelte';

	export let name;
</script>

<main>
	<h2>{name}</h2>
	<h1>Hello Abi!</h1>
	<YarnForm/>
	<Grid/>
</main>

<style>
	main {
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
		color: #000000;
		font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
	}

	h1 {
		font-variant: small-caps;
		font-size: 4em;
		font-weight: 500;
	}

	h2 {
		font-variant: small-caps;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>