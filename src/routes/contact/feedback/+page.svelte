<script>
	import Nav from '../../../Nav.svelte';
	import ContactForm from '../ContactForm.svelte';
	import Footer from '../../../Footer.svelte';
</script>

<svelte:head>
	<title>Feedback</title>
</svelte:head>

<Nav />

<main>
	<div class="content">
		<h1>Feedback</h1>
		<p>
			We'd love to hear from you! If you have any suggestions on what you'd like to see on
			the site, please fill out this form and let us know! We will send a response within
			48 hours.
		</p>
		<br>
		<ContactForm />
	</div>
</main>

<Footer />
