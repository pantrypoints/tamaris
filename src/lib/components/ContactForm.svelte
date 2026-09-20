<script>
	let name = $state('');
	let email = $state('');
	let phone = $state('');
	let message = $state('');
	let status = $state('idle'); // idle | sending | sent | error
	let errors = $state({});

	function validate() {
		const e = {};
		if (!name.trim()) e.name = 'Please enter your name.';
		if (!email.trim()) {
			e.email = 'Please enter your email.';
		} else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
			e.email = 'Please enter a valid email.';
		}
		if (!message.trim()) e.message = 'Tell us a bit about your inquiry.';
		errors = e;
		return Object.keys(e).length === 0;
	}

	async function handleSubmit(event) {
		event.preventDefault();
		if (!validate()) return;

		status = 'sending';

		try {
			const res = await fetch('https://pantrypoints.com/api/external', {
				method: 'POST',
				headers: {
					'Content-Type': 'application/json'
				},
				body: JSON.stringify({
					name: name.trim(),
					email: email.trim(),
					phone: phone.trim() || null,
					message: message.trim(),
					source: 'tamaris-restobar'
				})
			});

			if (!res.ok) throw new Error(`Request failed: ${res.status}`);

			status = 'sent';
			name = '';
			email = '';
			phone = '';
			message = '';
		} catch (err) {
			console.error('Inquiry submit failed:', err);
			status = 'error';
		}
	}
</script>

<!-- <script>
	let name = $state('');
	let email = $state('');
	let phone = $state('');
	let message = $state('');
	let status = $state('idle'); // idle | sending | sent | error
	let errors = $state({});

	function validate() {
		const e = {};
		if (!name.trim()) e.name = 'Please enter your name.';
		if (!email.trim()) {
			e.email = 'Please enter your email.';
		} else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
			e.email = 'Please enter a valid email.';
		}
		if (!message.trim()) e.message = 'Tell us a bit about your inquiry.';
		errors = e;
		return Object.keys(e).length === 0;
	}

	async function handleSubmit(event) {
		event.preventDefault();
		if (!validate()) return;

		status = 'sending';

		// TODO: Wire this up to your backend, email service (e.g. Formspree,
		// EmailJS) or a SvelteKit form action that emails/saves the inquiry.
		try {
			await new Promise((resolve) => setTimeout(resolve, 800));
			status = 'sent';
			name = '';
			email = '';
			phone = '';
			message = '';
		} catch (err) {
			status = 'error';
		}
	}
</script> -->

<section id="contact" class="section contact-section">
	<div class="container">
		<span class="eyebrow" style="display:block; text-align:center;">Reach Out</span>
		<h2 class="section-title">Send Us an Inquiry</h2>
		<p class="section-subtitle">
			Reservations, catering, or feedback — drop us a message and our team will get back to you.
		</p>

		<div class="contact-grid">
			<form onsubmit={handleSubmit} novalidate>
				<div class="field">
					<label for="name">Full Name</label>
					<input id="name" type="text" bind:value={name} placeholder="Juan Dela Cruz" />
					{#if errors.name}<span class="error">{errors.name}</span>{/if}
				</div>

				<div class="field-row">
					<div class="field">
						<label for="email">Email</label>
						<input id="email" type="email" bind:value={email} placeholder="you@email.com" />
						{#if errors.email}<span class="error">{errors.email}</span>{/if}
					</div>
					<div class="field">
						<label for="phone">Phone (optional)</label>
						<input id="phone" type="tel" bind:value={phone} placeholder="09XX XXX XXXX" />
					</div>
				</div>

				<div class="field">
					<label for="message">Message</label>
					<textarea
						id="message"
						rows="5"
						bind:value={message}
						placeholder="I'd like to reserve a table for 6 this Saturday at 7PM..."
					></textarea>
					{#if errors.message}<span class="error">{errors.message}</span>{/if}
				</div>

				<button type="submit" class="btn btn-primary" disabled={status === 'sending'}>
					{status === 'sending' ? 'Sending...' : 'Send Inquiry'}
				</button>

				{#if status === 'sent'}
					<p class="status success">Thanks! Your inquiry has been sent — we'll be in touch soon.</p>
				{:else if status === 'error'}
					<p class="status error-msg">Something went wrong. Please try calling us instead.</p>
				{/if}
			</form>

			<div class="details">
				<h3>Visit or Call Us</h3>
				<p>
					📍 Near China Bank, Gloria Diaz St.,<br />
					BF Resort Village, Las Piñas City,<br />
					Philippines, 1740
				</p>
				<p>📞 <a href="tel:09531606008">0953 160 6008</a></p>
				<p>
					👍 <a href="https://www.facebook.com/TamariGrills/" target="_blank" rel="noopener noreferrer">
						facebook.com/TamariGrills
					</a>
				</p>
			</div>
		</div>
	</div>
</section>

<style>
	.contact-section {
		background: var(--color-black-soft);
	}

	.contact-grid {
		display: grid;
		gap: 2.5rem;
		grid-template-columns: 1fr;
		max-width: 980px;
		margin: 0 auto;
	}

	form {
		background: var(--color-black-card);
		border: 1px solid rgba(245, 197, 24, 0.15);
		border-radius: var(--radius);
		padding: 2rem;
		display: flex;
		flex-direction: column;
		gap: 1.1rem;
	}

	.field {
		display: flex;
		flex-direction: column;
		gap: 0.4rem;
		flex: 1;
	}

	.field-row {
		display: flex;
		gap: 1rem;
		flex-direction: column;
	}

	label {
		font-size: 0.85rem;
		font-weight: 600;
		color: var(--color-muted);
	}

	input,
	textarea {
		background: var(--color-black);
		border: 1px solid rgba(255, 255, 255, 0.12);
		border-radius: 8px;
		padding: 0.7rem 0.9rem;
		color: var(--color-white);
		font-family: inherit;
		font-size: 0.95rem;
		resize: vertical;
	}

	input:focus,
	textarea:focus {
		outline: none;
		border-color: var(--color-yellow);
	}

	.error {
		color: #ff8a80;
		font-size: 0.8rem;
	}

	.status {
		margin: 0;
		font-size: 0.9rem;
		padding: 0.6rem 0.8rem;
		border-radius: 8px;
	}

	.status.success {
		background: rgba(31, 122, 61, 0.2);
		color: #8be8a4;
	}

	.status.error-msg {
		background: rgba(200, 60, 60, 0.15);
		color: #ff8a80;
	}

	.details {
		background: var(--color-green-dark);
		border-radius: var(--radius);
		padding: 2rem;
	}

	.details h3 {
		color: var(--color-yellow);
	}

	.details p {
		color: var(--color-white);
	}

	.details a {
		color: var(--color-yellow-soft);
		text-decoration: none;
	}

	.details a:hover {
		text-decoration: underline;
	}

	@media (min-width: 720px) {
		.field-row {
			flex-direction: row;
		}
	}

	@media (min-width: 860px) {
		.contact-grid {
			grid-template-columns: 1.4fr 1fr;
		}
	}
</style>
