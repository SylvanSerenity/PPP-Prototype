<script>
	import Nav from '../Nav.svelte';
	import Footer from '../Footer.svelte';
	import Slideshow from './Slideshow.svelte';
</script>

<Nav />

<main>
	<Slideshow />

	<h1>Home</h1>
</main>

<Footer />

<style>
	:global(:root) {
		--nav-height: 60px;
	}
	:global(*) {
		box-sizing: border-box;
		margin: 0;
	}
	:global(body) {
		margin-top: var(--nav-height);
		min-height: calc(100vh - var(--nav-height));

		display: flex;
		flex-direction: column;

		background-color: #bdbdbd;
	}
	:global(main) {
		flex: 1;
	}
</style>
