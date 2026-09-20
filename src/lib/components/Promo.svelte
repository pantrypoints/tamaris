<script>
	// Update this object whenever the current promo changes.
	const promo = {
		image: '/images/promo-3some-tbone.jpg',
		title: '3-Some T-Bone Treat',
		tag: 'Ongoing Promo',
		description:
			"Buy 2 T-Bone Steaks and get 1 FREE! Every order comes with rice and fries, grilled the Tamari's way.",
		validUntil: 'October 8, 2026',
		cta: { label: 'Ask About This Promo', href: '#contact' }
	};
</script>

<section id="promo" class="section promo">
	<div class="container">
		<span class="eyebrow">Limited Time</span>
		<h2 class="section-title">{promo.title}</h2>
		<p class="section-subtitle">{promo.description}</p>

		<div class="promo-card">
			<div class="promo-image">
				<img src={promo.image} alt={promo.title} />
			</div>
			<div class="promo-details">
				<span class="badge">{promo.tag}</span>
				<h3>{promo.title}</h3>
				<p>{promo.description}</p>
				<p class="valid">Offer valid until <strong>{promo.validUntil}</strong></p>
				<a href={promo.cta.href} class="btn btn-green">{promo.cta.label}</a>
			</div>
		</div>
	</div>
</section>

<style>
	.promo {
		background: var(--color-black-soft);
	}

	.promo-card {
		display: grid;
		grid-template-columns: 1fr;
		background: var(--color-black-card);
		border: 1px solid rgba(245, 197, 24, 0.15);
		border-radius: var(--radius);
		overflow: hidden;
		box-shadow: var(--shadow-lg);
		max-width: 960px;
		margin: 0 auto;
	}

	.promo-image {
		aspect-ratio: 4 / 3;
		overflow: hidden;
	}

	.promo-image img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.promo-details {
		padding: 2.25rem;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	.badge {
		align-self: flex-start;
		background: var(--color-yellow);
		color: var(--color-black);
		font-weight: 700;
		font-size: 0.75rem;
		text-transform: uppercase;
		letter-spacing: 0.06em;
		padding: 0.3rem 0.8rem;
		border-radius: 999px;
		margin-bottom: 0.75rem;
	}

	.promo-details h3 {
		color: var(--color-white);
		font-size: 1.6rem;
	}

	.promo-details p {
		color: var(--color-muted);
	}

	.valid {
		color: var(--color-yellow-soft);
		font-size: 0.9rem;
	}

	.promo-details .btn {
		align-self: flex-start;
		margin-top: 0.5rem;
	}

	@media (min-width: 760px) {
		.promo-card {
			grid-template-columns: 1fr 1fr;
		}
	}
</style>
