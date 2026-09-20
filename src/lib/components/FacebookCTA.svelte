<script>
	const fbUrl = 'https://www.facebook.com/TamariGrills/';
</script>

<section id="facebook" class="section fb-section">
	<div class="container fb-card">
		<div class="fb-icon" aria-hidden="true">
			<svg viewBox="0 0 24 24" width="46" height="46" fill="currentColor">
				<path
					d="M22 12.06C22 6.505 17.523 2 12 2S2 6.505 2 12.06c0 5.02 3.657 9.184 8.438 9.94v-7.03H7.898v-2.91h2.54V9.845c0-2.507 1.492-3.89 3.777-3.89 1.094 0 2.238.196 2.238.196v2.46h-1.26c-1.243 0-1.63.774-1.63 1.567v1.88h2.773l-.443 2.91h-2.33V22c4.78-.756 8.437-4.92 8.437-9.94Z"
				/>
			</svg>
		</div>
		<h2>Follow Us on Facebook</h2>
		<p>
			Get the latest promos, new menu drops, and behind-the-scenes moments from the Tamari's
			kitchen.
		</p>
		<a href={fbUrl} target="_blank" rel="noopener noreferrer" class="btn btn-primary">
			👍 Visit Our Facebook Page
		</a>
	</div>
</section>

<style>
	.fb-section {
		background: linear-gradient(135deg, var(--color-green-dark), var(--color-black-soft));
	}

	.fb-card {
		text-align: center;
		max-width: 600px;
	}

	.fb-icon {
		width: 84px;
		height: 84px;
		margin: 0 auto 1.25rem;
		display: flex;
		align-items: center;
		justify-content: center;
		border-radius: 50%;
		background: rgba(245, 197, 24, 0.12);
		color: var(--color-yellow);
	}

	.fb-card h2 {
		color: var(--color-white);
		font-size: clamp(1.6rem, 3.5vw, 2.2rem);
	}

	.fb-card p {
		color: var(--color-muted);
		margin-bottom: 1.75rem;
	}
</style>
