<script>
	import Nav from '../Nav.svelte';
	import Footer from '../Footer.svelte';
	import Slideshow from './Slideshow.svelte';

	const images = ["slideshow/cats.png", "slideshow/dogs.png", "slideshow/consultation.png"];
</script>

<Nav />

<main>
	<Slideshow {images} />

	<div class="content">
		<h1>About</h1>
		<p>Paradigm Pet Professionals...</p>
	</div>
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

		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	h1 {
		padding: 5px;
		text-align: center;
	}

	.content {
		max-width: 80%;
		padding: 10px;
	}
</style>
