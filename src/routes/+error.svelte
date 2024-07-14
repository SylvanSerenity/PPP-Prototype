<script>
	import { page } from '$app/stores';
	import Nav from '../Nav.svelte';
	import Footer from '../Footer.svelte';
</script>

<Nav />

<main>
	<div class="content">
		<h1>Something went wrong...</h1>
		<p>{$page.status ? $page.status + ': ' : ''}{$page.error? $page.error.message : 'An unknown error occurred.'}</p>
		<a href="/">Home</a>
	</div>
</main>

<Footer />

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	a {
		text-align: center;
		background-color: #003b6d;
		padding: 8px;
		border-radius: 10px;
		color: white;
		text-decoration: none;
	}
</style>
