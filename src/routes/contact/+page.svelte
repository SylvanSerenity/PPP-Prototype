<script>
	import Nav from '../../Nav.svelte';
	import ContactForm from './ContactForm.svelte';
	import Footer from '../../Footer.svelte';
</script>

<svelte:head>
	<title>Contact Us</title>
</svelte:head>

<Nav />

<main>
	<div class="content">
		<h1>Contact Us</h1>
		<p>
			If you would like to contact us directly, please feel free to fill out the form
			below, and we will get back to you within 48 hours.
		</p>
		<br>
		<ContactForm />
	</div>
</main>

<Footer />
