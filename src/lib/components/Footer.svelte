<script>
	const year = new Date().getFullYear();
</script>

<footer>
	<div class="container grid">
		<div class="brand-col">
			<img src="/images/logo.png" alt="Tamari's logo" />
			<p>Steak and Seafood Restobar — where every plate is a celebration.</p>
		</div>

		<div>
			<h4>Visit Us</h4>
			<p>
				Near China Bank, Gloria Diaz St.,<br />
				BF Resort Village, Las Piñas City,<br />
				Philippines, 1740
			</p>
		</div>

		<div>
			<h4>Get In Touch</h4>
			<p>
				<a href="tel:09531606008">📞 0953 160 6008</a><br />
				<a href="https://www.facebook.com/TamariGrills/" target="_blank" rel="noopener noreferrer">
					👍 facebook.com/TamariGrills
				</a>
			</p>
		</div>
	</div>

	<div class="container bottom">
		<p>© {year} Tamari's Steak and Seafood Restobar. All rights reserved.</p>
	</div>
</footer>

<style>
	footer {
		background: var(--color-black-soft);
		border-top: 3px solid var(--color-yellow);
		padding-top: 3.5rem;
	}

	.grid {
		display: grid;
		gap: 2.5rem;
		grid-template-columns: 1fr;
	}

	.brand-col img {
		height: 44px;
		margin-bottom: 0.75rem;
	}

	h4 {
		color: var(--color-yellow);
		font-family: var(--font-body);
		font-size: 1rem;
		text-transform: uppercase;
		letter-spacing: 0.06em;
	}

	a {
		text-decoration: none;
		color: var(--color-muted);
	}

	a:hover {
		color: var(--color-yellow);
	}

	.bottom {
		margin-top: 3rem;
		padding: 1.5rem;
		border-top: 1px solid rgba(255, 255, 255, 0.08);
		text-align: center;
		color: var(--color-muted);
		font-size: 0.85rem;
	}

	@media (min-width: 720px) {
		.grid {
			grid-template-columns: 1.3fr 1fr 1fr;
		}
	}
</style>
