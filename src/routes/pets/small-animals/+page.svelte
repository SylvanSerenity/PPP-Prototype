<script>
	import Nav from '../../../Nav.svelte';
	import Footer from '../../../Footer.svelte';
</script>

<svelte:head>
	<title>Small Animals</title>
</svelte:head>

<Nav />

<main>
	<div class="content">
		<img class="right" src="/small-animals/guinea-pigs.png" alt="Two guinea pigs eating">
		<h1>Small Animals</h1>
		<p>
			Sometimes, we want a pet in our lives but think it's impossible due to time constraints or limited
			space. In such cases, consider adopting a small animal like a chinchilla, ferret, gerbil, guinea
			pig, hamster, hermit crab, mouse, or even a snake! Depending on the type of animal you choose, you
			can create a comfortable habitat using small to large cages or glass aquariums. Essential amenities
			for your new pet include bedding or substrate, toys, an exercise wheel, a water dish or drip bottle,
			a food dish, and grooming supplies. Additionally, consider whether your pet will need a companion or
			if it will thrive on its own. Our "Pexperts" are here to help you choose the right pet and provide
			guidance on creating a happy home. <a href="/schedule-consultation">Schedule a consultation</a> with
			us today!
		</p>
		<img class="left" src="/small-animals/snake.png" alt="A snake smiling on a bed">
		<h2>Resources</h2>
		<p>
			Here are some resources to get you started:
		</p>
		<ul>
			<li><a href="https://chinchillacare.org/cage-habitat/" target="_blank">Chinchilla</a></li>
			<li><a href="https://www.thesprucepets.com/ferret-facts-1236789" target="_blank">Ferret</a></li>
			<li><a href="https://petgerbils.org/cage-habitat/" target="_blank">Gerbil</a></li>
			<li><a href="https://www.animalhumanesociety.org/adoption/guinea-pig-care" target="_blank">Guinea Pig</a></li>
			<li><a href="https://www.pdsa.org.uk/taking-care-of-your-pet/looking-after-your-pet/small-pets/the-ideal-home-for-your-hamster" target="_blank">Hamster</a></li>
			<li><a href="https://pethermitcrabs.org/cage-habitat/" target="_blank">Hermit Crab</a></li>
			<li><a href="https://www.bluecross.org.uk/pet-advice/caring-your-mouse" target="_blank">Mouse</a></li>
			<li><a href="https://www.snakesforpets.com/garter-snake-pet-care/" target="_blank">Snake</a></li>
		</ul>
	</div>
</main>

<Footer />

<style>
	img {
		max-width: 40%;
		max-height: 20%;
		margin: 25px;

		border: 1px solid #676767;
		border-radius: 8px;
		box-shadow: 2px 2px 5px 0px rgba(0, 0, 0, 0.2);
		transition: transform 0.3s ease;
	}
	img:hover {
		transform: scale(1.1);
	}
	.right {
		float: right;
	}
	.left {
		float: left;
	}
</style>
