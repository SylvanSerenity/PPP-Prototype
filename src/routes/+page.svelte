<script>
	import Nav from '../Nav.svelte';
	import Footer from '../Footer.svelte';
	import Slideshow from './Slideshow.svelte';

	const slides = [
		{src: '/slideshow/cats.png', text: 'Dreaming of a new feline companion? <a href="/pets/cats">Cats</a> are elegant, self-reliant, and loving, making them wonderful additions to any home.'},
		{src: '/slideshow/dogs.png', text: 'Thinking about adding a fun-loving, loyal pet to your family? <a href="/pets/dogs">Dogs</a> bring energy, affection, and joy to their owners, making them an excellent choice.'},
		{src: '/slideshow/ferret.png', text: 'Looking for a charming, smaller friend? <a href="/pets/small-animals">Small animals</a> like hamsters, guinea pigs, ferrets, and mice provide endless delight and are perfect for those who enjoy the company of little creatures.'},
		{src: '/slideshow/consultation.png', text: 'Looking for your new best friend? We are happy to help you navigate the adoption process!'}
	];
</script>

<svelte:head>
	<title>Paradigm Pet Professionals</title>
</svelte:head>

<Nav />

<main>
	<Slideshow {slides} />

	<div class="content">
		<h1>About Us</h1>
		<p>
			Pets are truly a gift from nature to humanity. Research has shown that welcoming a pet into our homes and hearts
			leads to longer, healthier lives for both us and our pets. At Pet Paradigm Professionals, our mission is to
			provide you with the resources needed to care for your beloved pets, whether they are furry, scaly, feathery, or
			slimy. Our team of pet experts, or "Pexperts", has been assisting pet owners and professionals for the past
			twelve years. They offer personalized consultations for current and future pet owners, as well as group
			presentations tailored for veterinary staff, pet shelters, and pet breeding professionals.
		</p>
		<h1>Services</h1>
		<p>
			Seeking basic pet care tips for the most popular types of pets? Unsure which pet is the best fit for your family?
			We are here to assist you with personalized, evidence-based pet care guidance, ensuring the lifelong health and
			well-being of your new companion. Feel free to explore our online resources or
			<a href="/schedule-consultation">schedule a consultation now</a>!
		</p>
		<p>
			Looking to add a feline friend to your family? If you're seeking a graceful, independent, and affectionate
			companion, explore our page dedicated to current and aspiring <a href="/pets/cats">cat owners</a>!
		</p>
		<p>
			Interested in welcoming a playful and loyal pet into your home? If a dog sounds like the perfect match, visit
			our page designed for current and future <a href="/pets/dogs">dog owners</a>!
		</p>
		<p>
			Considering a small and delightful pet to join your household? For those curious about small animals like
			hamsters, guinea pigs, ferrets, or even mice, check out our page tailored for
			<a href="/pets/small-animals">small animal enthusiasts</a>!
		</p>
	</div>
</main>

<Footer />
