<script lang="ts">
	import { onMount } from 'svelte';
	import { tweened } from 'svelte/motion';
	import { cubicInOut } from 'svelte/easing';

	// Errors
	let errors = {
		name: '',
		email: '',
		phone: '',
		pet: '',
		date: ''
	};;
	const emailPattern = /^[a-z0-9\.]+@[a-z0-9]+\.[a-z]+$/;
	const phonePattern = /^[0-9\-\+\(\)\s]+$/;

	// Pages
	let page = 0;
	const pages = ['contact', 'pets', 'schedule', 'comments'];

	function validatePage() {
		switch (pages[page]) {
			case 'contact': {
				return validateContact();
			}
			case 'pets': {
				return validatePets();
			}
			case 'schedule': {
				return validateSchedule();
			}
			default: return true;
		}
	}
	function nextPage() {
		if (validatePage()) page = (page + 1) % pages.length;
		upgradeProgress();
	}
	function previousPage() {
		if (page !== 0 || validateForm()) page = (pages.length + (page - 1)) % pages.length
		upgradeProgress();
	}

	// Contact page
	let name = '';
	let email = '';
	let phone = '';
	function validateName() {
		errors.name = '';

		if (name.trim() === '') {
			errors.name = '* Name is required.';
		}
	}
	function validateEmail() {
		errors.email = '';

		if (email.trim() === '') {
			errors.email = '* Email is required.';
		} else if (!emailPattern.test(email.toLocaleLowerCase())) {
			errors.email = '* Email must be valid.';
		}
	}
	function validatePhone() {
		errors.phone = '';

		if (phone.trim() === '') {
			errors.phone = '* Phone number is required.';
		} else if (!phonePattern.test(phone)) {
			errors.phone = '* Phone number must be valid.';
		} else if (phone.length < 10) {
			errors.phone = '* Phone number must be at least 10 digits.';
		}
	}
	function validateContact() {
		validateName();
		validateEmail();
		validatePhone();
		return !(errors.name || errors.email || errors.phone);
	}

	// Pets page
	let petSpecies = '';
	let petName = '';
	let petAge = 0;
	let pets: {
		petSpecies: string,
		petName: string,
		petAge: number
	}[] = [];
	function savePet() {
		if (petSpecies.trim() && petName.trim() && petAge >= 0) {
			pets = [...pets, ({ petSpecies, petName, petAge })];

			// Reset fields after submitting
			petSpecies = '';
			petName = '';
			petAge = 0;
		} else {
			errors.pet = '* All pet information is required.';
		}
	}
	function validatePets() {
		errors.pet = '';

		if (petSpecies.trim() || petName.trim() || petAge > 0) {
			errors.pet = '* Please save or remove pet information.';
			return false;
		}
		return true;
	}

	// Schedule page
	const timeZones = ['Pacific', 'Mountain', 'Central', 'Eastern'];
	let date = '';
	let timeZone = 'Pacific';
	function validateDate() {
		errors.date = '';

		if (!date) {
			errors.date = '* Date is required.';
		} else if (new Date() > new Date(date)) {
			errors.date = "* Date must be in the future."
		}
	}
	function validateSchedule() {
		validateDate();
		return !errors.date;
	}

	// Submit page
	let comments = '';
	function validateForm() {
		return validateContact() && validatePets() && validateSchedule();
	}
	function handleSubmit(event: SubmitEvent) {
		if (validateForm()) {
			const formData = new CustomEvent('submit', {
			detail: {
				name,
				email,
				phone,
				pets,
				comments
			}
			});
			dispatchEvent(formData);

			// Reset fields after submitting
			name = '';
			email = '';
			phone = '';
			pets = [];
			date = '';
			timeZone = 'Pacific';
			comments = '';
			alert('Scheduled Consultation!');

			// Return to start
			page = 0;
			upgradeProgress();
		}
		event.preventDefault();
	};

	// Progress bar
	const progress = tweened(0, {
		duration: 400,
		easing: cubicInOut
	});
	function upgradeProgress() {
		progress.set((page) / (pages.length - 1) * 100);
		console.log(progress);
	}
	onMount(upgradeProgress);
</script>

<style>
	.form-container {
		position: relative;
		padding: 20px;

		display: flex;
		align-items: center;
		justify-content: center;

		background-color: #676767;
		border-radius: 10px;
		box-shadow: 5px 5px 5px 0px rgba(0, 0, 0, 0.2);
		color: white;
		overflow: hidden;
	}

	.progress-bar-container {
		position: absolute;
		top: 0;
		width: 100%;
		height: 8px;
		background-color: lightgray;
	}
	.progress-bar {
		position: absolute;
		left: 0;
		height: 100%;
		background-color: #6699cc;
	}

	form {
		max-width: 100%;

		display: flex;
		flex-direction: column;
		align-items: center;
	}

	label {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
	}

	input, textarea {
		margin-bottom: 10px;
		padding: 8px;

		font-size: 1em;
		font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
	}
	textarea {
		max-width: 100%;
		max-height: 300px;
	}

	button {
		padding: 10px;
		margin-bottom: 10px;
		width: 80px;
		font-size: 1em;

		cursor: pointer;
		background-color: #6699cc;
		border: 2px solid #bdbdbd;
		border-radius: 6px;
		color: white;
		transition: transform 0.3s ease;
	}
	button:hover {
		transform: scale(1.05);
	}
	.page-selector {
		width: 100%;
		display: flex;
		justify-content: space-between;
	}

	.error {
		text-align: right;
		padding: 2px;

		color: red;
	}

	li {
		padding: 5px;
	}
	h2 {
		text-align: center;
	}
	p {
		text-align: center;
	}
	.header {
		align-self: center;
		width: 80%;
	}
</style>

<div class="form-container">
	<div class="progress-bar-container">
		<span class="progress-bar" style="width: {$progress}%"></span>
	</div>
	<form onsubmit={handleSubmit}>
		{#if page === 0}
			<div class="header">
				<h2>Contact Info</h2>
				<p>Please provide contact information for us to contact you about your consultation.</p>
			</div>
			<label>
				Name:
				<input type="text" placeholder="John Doe" bind:value={name}  oninput={validateName} required />
				<span class="error">{errors.name}</span>
			</label>
			<label>
				Email:
				<input type="email" placeholder="email@domain.ext" bind:value={email} oninput={validateEmail} required />
				<span class="error">{errors.email}</span>
			</label>
			<label>
				Phone Number:
				<input type="tel" placeholder="(555) 555-5555" bind:value={phone} oninput={validatePhone} required />
				<span class="error">{errors.phone}</span>
			</label>
		{:else if page === 1}
			<div class="header">
				<h2>Pet Info</h2>
				<p>If you have any pets that are the topic of the consultation, please provide their information below.</p>
			</div>
			<label>
				Species:
				<input type="text" placeholder="Dog" bind:value={petSpecies} required />
			</label>
			<label>
				Name:
				<input type="text" placeholder="Spot" bind:value={petName} required />
			</label>
			<label>
				Age:
				<input type="number" placeholder="3" bind:value={petAge} required />
			</label>
			<span class="error">{errors.pet}</span>
			<button type="button" onclick={savePet}>Save</button>
			<ul>
				{#each pets as pet}
					<li>{pet.petAge}-year-old {pet.petName} the {pet.petSpecies}</li>
				{/each}
			</ul>
		{:else if page === 2}
			<div class="header">
				<h2>Consultation Date</h2>
				<p>Please schedule a date for the consultation. We will contact you with available times on your requested date.</p>
			</div>
			<label>
				Date:
				<input type="date" bind:value={date}  oninput={validateDate} required />
				<span class="error">{errors.date}</span>
			</label>
			<label>
				Time Zone:
				<select bind:value={timeZone}  required>
					{#each timeZones as tz}
						<option value={tz} selected={tz === timeZone}>{tz}</option>
					{/each}
				</select>
			</label>
		{:else if page === 3}
			<div class="header">
				<h2>Additional Comments</h2>
				<p>Feel free to leave any more information for your Pexpert!</p>
			</div>
			<label>
				Comments:
				<textarea placeholder="Hello!" bind:value={comments}></textarea>
			</label>
		{/if}
		<div class="page-selector">
			<button type="button" onclick={previousPage}>Previous</button>
			{#if page !== (pages.length - 1)}
				<button type="button" onclick={nextPage}>Next</button>
			{:else}
				<button type="submit">Submit</button>
			{/if}
		</div>
	</form>
</div>
