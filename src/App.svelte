<script>
	import Grid from './Grid.svelte'
	import YarnForm from './YarnForm.svelte';

	export let name;

	const scrollToForm = () => {
		document.body.scrollTop = 0;
		document.documentElement.scrollTop = 0;
	}
</script>

<main>
	<h1>{name}</h1>
	<h2>Hello Abi!</h2>
	<div>
		<p>
			<b> Here's how you use Windr: </b>
		<p/>
		<ol>
			<li>
				Fill out the form below to make a new yarn entry
			</li>
			<li>
				Edit <i>Count</i> if the amount changes
			</li>
			<li>
				Delete if you make a mistake or run out
			</li>
		</ol>
	</div>
	<YarnForm/>
	<Grid/>
	<div class="formNav" on:click={scrollToForm}>&#8593;</div>
</main>

<style>
	.formNav {
		position: fixed;
		bottom: 0;
		right: 0.5rem;
		/* content: "\2191"; */
		font-size: 3em;
		color: black;
		padding: 0 1rem;
	}
	.formNav:hover {
		cursor: pointer;
	}
	html {
		scroll-behavior: smooth;
	}
	main {
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
		max-width: 240px;
		margin: 0 auto;
		color: #000000;
		font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
	}

	h1 {
		font-variant: small-caps;
		font-size: 4em;
		font-weight: 500;
		white-space: nowrap;
		padding: 1rem 3rem;
		border: 0.25rem solid black;
	}

	h2 {
		margin-top: -1rem;
		margin-bottom: 3rem;
		font-variant: small-caps;
	}

	h2::after {
		content: "";
		display: block;
		margin-top: 0.25rem;
		border-top: 0.1rem solid black;
		border-bottom: 0.1rem solid black;
	}

	ol {
		text-align: left;
		line-height: 2em;
		margin-bottom: 2rem;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>