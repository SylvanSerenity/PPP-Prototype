<script>
	import Nav from '../Nav.svelte';
	import Footer from '../Footer.svelte';
	import Slideshow from './Slideshow.svelte';

	const images = ["/slideshow/cats.png", "/slideshow/dogs.png", "/slideshow/ferret.png", "/slideshow/consultation.png"];
</script>

<Nav />

<main>
	<Slideshow {images} />

	<div class="content">
		<h1>About</h1>
		<p>
			Pets are nature's gift to humanity. It has been scientifically proven that opening our homes and hearts to a pet
			increases our longevity and improves our overall quality of life as well as the lives of our pets. At Pet Paradigm
			Professionals, our mission is to offer resources to help you care for your furry, scaly, feathery, and slimy loved
			ones. Our pet experts—or “Pexperts”—have been working with pet owners and professionals alike for the past twelve
			years. They offer one-on-one consultations with current and prospective pet owners as well as group presentations
			designed for veterinary, pet shelter, and pet breeding professionals.
		</p>
		<h1>Services</h1>
		<p>
			Looking for basic pet care advice for the most common type of pets? Need additional help determining which type of
			pet is right for you and your family? We will work with you and provide tailored evidence-based pet care to ensure
			lifelong health and wellness of your new companion.
		</p>
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

	:global(.content) {
		width: 80%;
		margin: 20px;
	}
	@media screen and (min-width:920px) {
		:global(.content) {
			max-width: 50%;
		}
	}

	h1 {
		padding: 5px;
		text-align: center;
	}
	p {
		padding: 5px;
		margin-bottom: 10px;
	}
</style>
