<script lang="ts">
	import { onMount, onDestroy } from 'svelte';

	export let slides: {
		src: string,
		text: string
	}[];
	let slideIndex = 0;
	let interval: number;
	const intervalDuration = 5000;

	function resetInterval() {
		clearInterval(interval);
		interval = setInterval(() => {
			nextSlide();
		}, intervalDuration);
	}

	function nextSlide() {
		// Loop at the end of the slideshow
		slideIndex = (slideIndex + 1) % slides.length;
		resetInterval();
	}
	function previousSlide() {
		// Loop at the beginning of the slideshow
		slideIndex = (slides.length + (slideIndex - 1)) % slides.length;
		resetInterval();
	}
	function setSlide(index: number) {
		// Loop at the beginning of the slideshow
		slideIndex = index;
		resetInterval();
	}

	// Progress slides
	onMount(() => {
		clearInterval(interval);
		interval = setInterval(() => {
			nextSlide();
		}, intervalDuration);
	});

	onDestroy(() => {
		clearInterval(interval);
	});

	function setSlideProgression(yes: boolean) {
		if (yes) {
			// Clear in the case that the user is hovering on page load
			clearInterval(interval);
			interval = setInterval(() => {
				nextSlide();
			}, intervalDuration);
		} else clearInterval(interval);
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
		z-index: 5;
		padding: 16px;

		cursor: pointer;
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
		z-index: 5;

		display: flex;
		align-items: center;
		justify-content: center;
	}

	.indicator {
		height: 12px;
		width: 12px;
		margin: 0 2px;

		cursor: pointer;
		background-color: #67676767;
		border: 1px solid white;
		border-radius: 50%;
		display: inline-block;
		transition: background-color 0.3s ease;
	}

	.indicator.active {
		background-color: #bdbdbdbd;
	}

	.slide-text {
		position:absolute;
		max-width: 35%;
		right: 16px;
		bottom: 8px;
		padding: 8px;
		z-index: 1;

		background-color: rgba(0, 0, 0, 0.5);
		border-radius: 4px;
		color: #bdbdbd;
	}

	.cta {
		position: absolute;
		left: 50%;
		top: 50%;
		transform: translate(-50%, -50%) scale(1);
		padding: 10px;
		text-align: center;

		font-size: 20px;
		background-color: #003b6d;
		border-radius: 16px;
		font-size: 28px;
	}
	.cta:hover {
		transform: translate(-50%, -50%) scale(1.1);
	}
	.cta a {
		text-decoration: none;
		color: white;
	}
	.cta a::after {
		position: absolute;
		left: 50%;
		bottom: 8px;
		width: 0;
		height: 2px;
		background-color: white;
		transition: width 0.3s ease, left 0.3s ease;

		content: '';
	}
	.cta a:hover::after {
		width: 90%;
		left: 5%;
	}

	:global(.slide-text a) {
		color: #bdbdbd;
	}
</style>

<div class="slideshow-container">
	{#each slides as slide, index}
		<div role="button" aria-label="Hover box" tabindex="0" class:active={index === slideIndex} class="slide" onmouseenter={() => setSlideProgression(false)} onmouseleave={() => setSlideProgression(true)}>
			<img src={slide.src} alt="Slide {index + 1}">
			<div class="slide-text">{@html slide.text}</div>
			{#if index === (slides.length - 1)}
				<span class="cta"><a href="/schedule-consultation">Schedule Consultation Now!</a></span>
			{/if}
		</div>
	{/each}
	<button type="button" class="previous" onclick={previousSlide}>&#10094;</button>
	<button type="button" class="next" onclick={nextSlide}>&#10095;</button>
	<div class="indicator-container">
		{#each slides as _, index}
			<button type="button" class="indicator {index === slideIndex ? 'active' : ''}" onclick={() => setSlide(index)}></button>
		{/each}
	</div>
</div>