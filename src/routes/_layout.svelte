<script>
	import Nav from '../components/Nav.svelte';

	export let segment;
</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;700&display=swap');
	
	/*main {
		position: relative;
		max-width: 56em;
		background-color: white;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
	}*/
</style>

<Nav {segment}/>

<main>
	<slot></slot>
</main>