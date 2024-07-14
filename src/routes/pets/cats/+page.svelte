<script>
	import Nav from '../../../Nav.svelte';
	import Footer from '../../../Footer.svelte';
</script>

<svelte:head>
	<title>Cats</title>
</svelte:head>

<Nav />

<main>
	<div class="content">
		<h1>Cats</h1>
		<img class="right" src="/cats/cat-field.png" alt="Cat in field">
		<p>
			Cats were domesticated around 7500 BCE in Western Asia and have become the second most popular
			pet in the United States. With over 60 documented cat breeds, care and dietary needs can vary
			among them. However, there are some general diet and care practices that are beneficial for
			the health and well-being of your feline family member, regardless of their breed.
		</p>
		<h2>0-4 Weeks</h2>
		<p>
			It is crucial for a queen (a pregnant or nursing female cat) to nurse her kittens directly if
			possible. Closely monitor the growth of your kitten to ensure a steady growth rate. If a kitten
			is not growing adequately, a caretaker may need to feed it directly using a bottle or feeding
			tube. Factors that can affect a kitten's weight gain include:
		</p>
		<ul>
			<li>Competition from too many siblings for the mother’s milk</li>
			<li>Gastrointestinal diseases</li>
			<li>Environmental conditions such as extreme heat, cold, or unsanitary environments</li>
		</ul>
		<img class="left" src="/cats/cat-stairs.png" alt="Cat on stairs">
		<h2>4 Weeks to 1 Year</h2>
		<p>
			Around three to four weeks after birth, kittens can begin eating soft wet kitten food. The ASPCA
			recommends that kittens at this age consume 1/2 a cup to 1 cup of dry kitten food or 6-9 ounces
			of wet kitten food daily. If your kitten struggles with hard food, add a small amount of water
			to soften it. Kitten-specific food provides the essential nutrients needed for growth, energy,
			and overall health. Since dietary needs can vary by breed, consult your veterinarian for specific
			recommendations.
		</p>
		<h2>1-7 Years</h2>
		<p>
			Once kittens reach one year, they transition into the cat stage and require fewer nutrients. Their
			activity levels and metabolism decrease. It is advisable not to leave food out all day; instead,
			provide meals a couple of times a day to prevent constant snacking. This approach helps reduce the
			risk of obesity and other weight-related health issues in cats.
		</p>
		<h2>7+ Years</h2>
		<p>
			As cats age, their bodies undergo significant changes and begin to deteriorate. Older cats should
			consume fewer fats and calories but more high-quality proteins. When buying packaged food, look for
			products that specify a particular protein (e.g., "salmon") rather than a generic category (e.g.,
			"fish"). Specific proteins indicate higher quality compared to byproducts or mixed proteins of
			lesser quality.
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
