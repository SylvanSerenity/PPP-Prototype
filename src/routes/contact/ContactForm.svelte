<script lang="ts">
	let name = '';
	let email = '';
	let message = '';
	let errors = {
		name: '',
		email: '',
		message: ''
	};
	const emailPattern = /^[a-z0-9\.]+@[a-z0-9]+\.[a-z]+$/;

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

	function validateMessage() {
		errors.message = '';

		if (message.trim() === '') {
			errors.message = '* Message is required.';
		}
	}

	function validateForm() {
		validateName();
		validateEmail();
		validateMessage();
		return !(errors.name || errors.email || errors.message);
	}

	function handleSubmit(event: SubmitEvent) {
		if (validateForm()) {
			const formData = new CustomEvent('submit', {
			detail: {
				name,
				email,
				message
			}
			});
			dispatchEvent(formData);

			// Reset fields after submitting
			name = '';
			email = '';
			message = '';
			alert('Sent!');
		}
		event.preventDefault();
	};
</script>

<style>
	.form-container {
		width: 100%;

		display: flex;
		align-items: center;
		justify-content: center;
	}

	form {
		max-width: 100%;

		display: flex;
		flex-direction: column;
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

	.error {
		text-align: right;

		color: red;
	}
</style>

<div class="form-container">
	<form onsubmit={handleSubmit}>
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
			Message:
			<textarea placeholder="Hello!" bind:value={message} oninput={validateMessage} required></textarea>
			<span class="error">{errors.message}</span>
		</label>
		<button type="submit">Submit</button>
	</form>
</div>
