<script>
	// NOTE: Prices marked "approx." are placeholders — replace with your
	// actual menu prices. Baby Squid Kebab's price of 168 is confirmed.
	const dishes = [
		{
			name: 'Baby Squid Kebab (3pcs)',
			price: '₱168',
			image: '/images/dish-baby-squid-kebab.jpg',
			description: 'Char-grilled baby squid skewers, served with a citrus dipping sauce.'
		}
		// {
		// 	name: 'T-Bone Jumbo Steak',
		// 	price: '₱588',
		// 	priceNote: 'approx.',
		// 	image: '/images/promo-3some-tbone.jpg',
		// 	description: "Our awesome pride — a hefty jumbo T-bone grilled to your liking, with rice and fries."
		// },
		// {
		// 	name: 'Cajun Seafood Boil',
		// 	price: '₱850',
		// 	priceNote: 'approx.',
		// 	image: '/images/promo-mothers-day.jpg',
		// 	description: 'Shrimp, mussels, and crab tossed in bold Cajun spices with sweet corn.'
		// },
		// {
		// 	name: 'Crispy Pata',
		// 	price: '₱650',
		// 	priceNote: 'approx.',
		// 	image: '/images/promo-mothers-day.jpg',
		// 	description: 'Deep-fried pork leg, crackling skin outside, tender meat inside — a Filipino favorite.'
		// }
	];

	let index = $state(0);
	let autoplayId;

	function next() {
		index = (index + 1) % dishes.length;
	}

	function prev() {
		index = (index - 1 + dishes.length) % dishes.length;
	}

	function goTo(i) {
		index = i;
	}

	$effect(() => {
		autoplayId = setInterval(next, 5000);
		return () => clearInterval(autoplayId);
	});
</script>

<section id="menu" class="section carousel-section">
	<div class="container">
		<span class="eyebrow" style="display:block; text-align:center;">Fan Favorites</span>
		<h2 class="section-title">Our Best Dishes</h2>
		<p class="section-subtitle">
			A taste of what keeps our regulars coming back to BF Resort Village.
		</p>

		<div
			class="carousel"
			role="region"
			aria-label="Best dishes carousel"
			onmouseenter={() => clearInterval(autoplayId)}
			onmouseleave={() => (autoplayId = setInterval(next, 5000))}
		>
			<button class="nav-btn prev" onclick={prev} aria-label="Previous dish">‹</button>

			<div class="track">
				{#each dishes as dish, i (dish.name)}
					<article class="slide" class:active={i === index}>
						<div class="slide-image">
							<img src={dish.image} alt={dish.name} />
						</div>
						<div class="slide-info">
							<h3>{dish.name}</h3>
							<p>{dish.description}</p>
							<span class="price">
								{dish.price}
								{#if dish.priceNote}<small>({dish.priceNote})</small>{/if}
							</span>
						</div>
					</article>
				{/each}
			</div>

			<button class="nav-btn next" onclick={next} aria-label="Next dish">›</button>
		</div>

		<div class="dots">
			{#each dishes as dish, i (dish.name)}
				<button
					class="dot"
					class:active={i === index}
					onclick={() => goTo(i)}
					aria-label={`Show ${dish.name}`}
				></button>
			{/each}
		</div>
	</div>
</section>

<style>
	.carousel-section {
		background: var(--color-black);
	}

	.carousel {
		position: relative;
		display: flex;
		align-items: center;
		gap: 1rem;
	}

	.track {
		position: relative;
		flex: 1;
		min-height: 480px;
		border-radius: var(--radius);
		overflow: hidden;
	}

	.slide {
		position: absolute;
		inset: 0;
		opacity: 0;
		pointer-events: none;
		transition: opacity 0.5s ease;
		display: grid;
		grid-template-rows: auto 1fr;
		background: var(--color-black-card);
		border: 1px solid rgba(245, 197, 24, 0.12);
		border-radius: var(--radius);
		overflow: hidden;
	}

	.slide.active {
		opacity: 1;
		pointer-events: auto;
		position: relative;
	}

	.slide-image {
		height: 300px;
		overflow: hidden;
	}

	.slide-image img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.slide-info {
		padding: 1.5rem 1.75rem;
		display: flex;
		flex-direction: column;
		gap: 0.4rem;
	}

	.slide-info h3 {
		color: var(--color-white);
		font-size: 1.4rem;
	}

	.slide-info p {
		color: var(--color-muted);
		margin-bottom: 0.25rem;
	}

	.price {
		color: var(--color-yellow);
		font-weight: 700;
		font-size: 1.3rem;
	}

	.price small {
		color: var(--color-muted);
		font-weight: 500;
		font-size: 0.75rem;
	}

	.nav-btn {
		flex-shrink: 0;
		width: 44px;
		height: 44px;
		border-radius: 50%;
		border: 2px solid var(--color-yellow);
		background: transparent;
		color: var(--color-yellow);
		font-size: 1.5rem;
		line-height: 1;
		display: none;
		align-items: center;
		justify-content: center;
		transition:
			background 0.2s ease,
			color 0.2s ease;
	}

	.nav-btn:hover {
		background: var(--color-yellow);
		color: var(--color-black);
	}

	.dots {
		display: flex;
		justify-content: center;
		gap: 0.6rem;
		margin-top: 1.5rem;
	}

	.dot {
		width: 10px;
		height: 10px;
		border-radius: 50%;
		border: none;
		background: rgba(255, 255, 255, 0.25);
		padding: 0;
	}

	.dot.active {
		background: var(--color-yellow);
	}

	@media (min-width: 720px) {
		.slide {
			grid-template-columns: 1fr 1fr;
			grid-template-rows: none;
		}
		.slide-image {
			height: 100%;
		}
		.nav-btn {
			display: flex;
		}
	}
</style>
