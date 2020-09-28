<script>
	import Nav from '../components/Nav.svelte';

	export let segment;
</script>

<style>
	main {
		position: relative;
		height: 98vh;
		max-width: 56em;
		background-color: var(--card-color);
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		text-align: center;
	}
</style>

<Nav {segment}/>

<main>
	<slot></slot>
</main>

<footer>Made By Daniel Brown 😘</footer>