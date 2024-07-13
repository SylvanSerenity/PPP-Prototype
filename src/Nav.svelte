<script>
	let searchVisible = false;
</script>

<nav>
	<ul class="nav-section">
		<li><a class="nav-item" href="/"><img src="/favicon.png" alt="Logo"><span class="nav-link">Home</span></a></li>
		<li class="dropdown nav-item">
			<span class="nav-link">Pets</span>
			<ul class="dropdown-menu">
				<li class="nav-item"><a href="/pets/cats">Cats</a></li>
				<li class="nav-item"><a href="/pets/dogs">Dogs</a></li>
				<li class="nav-item"><a href="/pets/small-animals">Small Animals</a></li>
			</ul>
		</li>
	</ul>
	<div class="nav-section">
		<span class="cta"><a class="nav-link" href="/schedule-consultation">Schedule Consultation</a></span>
	</div>
</nav>
<div class="search-container">
	<label><input class:active={searchVisible} class="search-field" type="text" placeholder="Search..." /></label>
	<button class="search-icon" type="button" onclick={() => searchVisible = !searchVisible}>?</button>
</div>

<style>
	* {
		padding: 0;
	}

	nav {
		top: 0;
		position: fixed;
		z-index: 100;
		width: 100%;
		height: var(--nav-height);
		max-height: var(--nav-height);

		display: flex;
		justify-content: space-between;
		align-items: center;

		background-color: #003b6d;
		color: white;
	}

	li img {
		height: 2rem;
		margin-right: 10px;
	}

	img {
		height: calc(var(--nav-height) - 6px);
	}

	ul {
		list-style: none;
	}

	a {
		display: flex;
		align-items: center;

		text-decoration: none;
		color: white;
	}

	.nav-section {
		height: 100%;

		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	.nav-item {
		margin-right: 15px;
		padding: 10px;
		height: 100%;

		display: flex;
		align-items: center;
	}

	.nav-link {
		position: relative;
		cursor: pointer;
		padding-bottom: 2px;
	}
	
	.nav-link::after {
		position: absolute;
		left: 50%;
		bottom: 0;
		width: 0;
		height: 2px;
		background-color: white;
		transition: width 0.3s ease, left 0.3s ease;

		content: '';
	}
	
	.nav-item:hover .nav-link::after, .nav-link:hover::after {
		width: 100%;
		left: 0;
	}

	.dropdown {
		height: 100%;

		display: flex;
		align-items: center;

		-webkit-user-select: none;
		-ms-user-select: none;
		user-select: none;
	}

	.dropdown-menu {
		position: absolute;
		margin-left: -10px;

		display: none;

		box-shadow: 2px 2px 5px 0px rgba(0, 0, 0, 0.2);
	}

	@media screen and (min-width: 480px) {
		.dropdown:hover {
			width: 110px;
		}
	}

	.dropdown:hover .dropdown-menu {
		position: fixed;
		top: var(--nav-height);

		display:block;

		background-color: #003b6d;
	}

	.dropdown-menu .nav-item {
		margin: 0;
	}

	.dropdown-menu .nav-item:hover {
		background-color: rgba(0, 0, 0, 0.2);
	}

	.cta {
		margin-right: 15px;
		padding: 10px;

		border: 1px solid white;
		border-radius: 18px;
		transition: transform 0.3s ease;
		font-weight: bold;
	}
	.cta:hover {
		transform: scale(1.05);
	}

	.search-container {
		position: fixed;
		right: 0;
		margin: 8px;
		z-index: 100;
	}

	.search-icon {
		width: 1.5rem;
		height: 1.5rem;
		background-color: #003b6d;
		border: 1px solid white;
		color: white;
	}

	.search-container input {
		height: 1.5rem;
		padding: 2px;
	}

	.search-field {
		display: none;
	}

	.active {
		display: inline-block;
	}
</style>
