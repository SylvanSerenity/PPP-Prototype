<script lang="ts">
	const images = ["slideshow/cats.png", "slideshow/dogs.png", "slideshow/consultation.png"];
	let imageIndex = 0;
	let direction = 'next';

	function nextSlide() {
		// Loop at the end of the slideshow
		imageIndex = (imageIndex + 1) % images.length;
		direction = 'next';
	}
	function previousSlide() {
		// Loop at the beginning of the slideshow
		imageIndex = (images.length + (imageIndex - 1)) % images.length;
		direction = 'previous';
	}
	function setSlide(index: number) {
		// Loop at the beginning of the slideshow
		imageIndex = index;
		direction = (index > imageIndex) ? 'next' : 'previous';
	}
</script>

<style>
	.slideshow-container {
		position: relative;
		width: 100%;
		height: 75vh;
		overflow: hidden;
	}

	.slide {
		width: 100%;
		height: 100%;

		display: none;
	}

	.active {
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.previous, .next {
		position: absolute;
		top: calc(50% - calc(var(--nav-height) / 2));
		height: var(--nav-height);
		z-index: 1;
		padding: 16px;

		background-color: #67676742;
		border-radius: 0 3px 3px 0;
		color: white;
		font-weight: bold;
		transition: 0.3s ease;

		-webkit-user-select: none;
		-ms-user-select: none;
		user-select: none;
	}

	.next {
		right: 0;
		border-radius: 3px 0 0 3px;
	}

	.previous:hover, .next:hover {
		background-color: rgba(0, 0, 0, 0.2);
	}

	img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		object-position: 80% 25%;
	}

	.indicator-container {
		position: absolute;
		bottom: 8px;
		width: 100%;
		z-index: 1;

		display: flex;
		align-items: center;
		justify-content: center;
	}

	.indicator {
		height: 12px;
		width: 12px;
		margin: 0 2px;

		background-color: #67676767;
		border: 1px solid white;
		border-radius: 50%;
		display: inline-block;
		transition: background-color 0.3s ease;
	}

	.indicator.active {
		background-color: #bdbdbdbd;
	}
</style>

<div class="slideshow-container">
	{#each images as src, index}
		<div class:active={index === imageIndex} class="slide">
			<img {src} alt="Slide {index + 1}">
		</div>
	{/each}
	<button type="button" class="previous" onclick={previousSlide}>&#10094;</button>
	<button type="button" class="next" onclick={nextSlide}>&#10095;</button>
	<div class="indicator-container">
		{#each images as _, index}
			<button type="button" class="indicator {index === imageIndex ? 'active' : ''}" onclick={() => setSlide(index)}></button>
		{/each}
	</div>
</div>