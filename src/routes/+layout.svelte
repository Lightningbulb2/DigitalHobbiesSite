<script>
	import Header from './Header.svelte';
	import './styles.css';
	import "../lib/styles/global.scss"
</script>

<div class="app">
	<Header class="header" />

	<main class="bg-dark text-white">
		<div class="container">
			<slot />
		</div>
	</main>


</div>

<style>

	.app {
		height: 100vh;
		display: flex;
		flex-direction: column;
	}

	.header {
		flex-shrink: 1;
	}


	main {
		flex-grow: 1;
	}
</style>