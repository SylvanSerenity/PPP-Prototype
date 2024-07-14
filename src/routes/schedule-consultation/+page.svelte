<script>
	import Nav from '../../Nav.svelte';
	import ConsultForm from './ConsultForm.svelte';
	import Footer from '../../Footer.svelte';
</script>

<svelte:head>
	<title>Schedule Consultation</title>
</svelte:head>

<Nav />

<main>
	<div class="content">
		<h1>Schedule Consultation</h1>
		<p>
			Searching for your new best friend? The following organizations can help you find and adopt the perfect companion:
		</p>
		<ul>
			<li><a href="https://home-home.org/" target="_blank">General Adoption Resources</a></li>
			<li><a href="https://www.aspca.org/ " target="_blank">ASPCA</a></li>
			<li><a href="https://www.sterlingshelter.org/humane-society/koi-fish-rescue/" target="_blank">Fish Rescue</a></li>
			<li><a href="https://savethesnakes.org/snakerescuecall/" target="_blank">Snake Rescue</a></li>
			<li><a href="https://ftlob.rescuegroups.org/" target="_blank">Bird Rescue</a></li>
		</ul>
		<br>
		<p>
			We are also happy to help you navigate the adoption process! We will guide you through each step in the process from
			determining which type of pet is best suited for your family and home environment, to completing the necessary paperwork,
			to bringing your new loved one home. Please fill out our contact form to request a consultation. We will contact you
			within 48 hours to schedule a consultation. All fields are required.
		</p>
		<br>
		<ConsultForm />
	</div>
</main>

<Footer />
