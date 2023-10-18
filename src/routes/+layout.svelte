<script>
	import Header from './Header.svelte';
	import './styles.css';
</script>

<div class="app">
	<Header />

	<main class="bg-dark text-white">
		<div class="container">
			<slot />
		</div>
	</main>


</div>

<style>
	.app {
		height: 100vh;
	}

	main {
		height: 100%;

	}
</style>