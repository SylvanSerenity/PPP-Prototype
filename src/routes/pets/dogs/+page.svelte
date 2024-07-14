<script>
	import Nav from '../../../Nav.svelte';
	import Footer from '../../../Footer.svelte';
</script>

<svelte:head>
	<title>Dogs</title>
</svelte:head>

<Nav />

<main>
	<div class="content">
		<h1>Dogs</h1>
		<img class="left" src="/dogs/dog.png" alt="A dog">
		<p>
			The domestic dog is a highly social animal, offering a vast array of choices with over 300
			breeds recognized by the World Canine Organization. Adopting a dog provides mutual benefits
			for both the dog and the owner, with numerous studies highlighting the social advantages of
			companionship and reduced feelings of loneliness. Additionally, research shows medical benefits
			such as lower blood pressure and improved lipid profiles. If you have a dog, it is essential to
			ensure proper care, including a balanced diet and sufficient exercise. This page provides
			detailed information on caring for your pets throughout their different life stages.
		</p>
		<h2>Diet & Exercise</h2>
		<p>
			Dogs’ dietary needs change as they mature. Puppies should be nursed for the first 2 months, then
			transitioned to three meals per day from three to six months old. Their food intake should be
			reduced to two meals per day from six months to one year old, and finally to one meal per day
			after one year old. It is crucial to keep your dog hydrated, as their body mass is composed of
			60-70% water. According to the ASPCA, a 10% decrease in body water can cause illness, and a 15%
			loss can be fatal.
		</p>
		<p>
			Like humans, dogs require regular physical activity to maintain organ health and overall
			well-being. Exercise needs vary by breed and size, but generally, 30 to 120 minutes of exercise
			per day is recommended. This can include brisk walks or playtime with toys that encourage physical
			activity, ensuring they are age-appropriate and do not pose choking hazards.
		</p>
		<img class="right" src="/dogs/dogs.png" alt="Two dogs together">
		<h2>Grooming & Handling</h2>
		<p>
			Maintaining your dog’s cleanliness is vital for its health. Regular brushing reduces shedding and
			prevents matted fur, which can be challenging to remove. Check for ticks and fleas, especially after
			outdoor activities in wooded areas. Bathing is also essential; ensure you rinse all soap to prevent
			rashes and use dog-specific shampoo to avoid allergic reactions. Handle your dog with care,
			supporting its body appropriately based on its size. For small dogs, cradle them with one hand under
			the chest and the forearm supporting the back half. For larger dogs, use both arms to support the
			chest and rear when lifting.
		</p>
		<h2>Vaccinations & Medications</h2>
		<p>
			Consult your veterinarian for the recommended vaccinations, which typically include core vaccines
			for diseases such as hepatitis, rabies, and parvovirus. Additional vaccines may be necessary based
			on your dog's environment, such as Bordetella bronchiseptica, Borrelia burgdorferi, and Leptospira
			bacteria. Always follow your vet’s advice to ensure your dog’s health and safety.
		</p>
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
