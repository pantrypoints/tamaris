<script>
	let menuOpen = $state(false);

	const links = [
		{ href: '#promo', label: 'Promo' },
		{ href: '#menu', label: 'Menu' },
		{ href: '#facebook', label: 'Facebook' },
		{ href: '#contact', label: 'Contact' }
	];

	let scrolled = $state(false);

	$effect(() => {
		function onScroll() {
			scrolled = window.scrollY > 12;
		}
		window.addEventListener('scroll', onScroll);
		return () => window.removeEventListener('scroll', onScroll);
	});

	function closeMenu() {
		menuOpen = false;
	}
</script>

<header class:scrolled>
	<div class="container bar">
		<a href="#top" class="brand">
			<img src="/images/logo.png" alt="Tamari's Steak and Seafood Restobar" />
		</a>

		<nav class="desktop-nav">
			{#each links as link (link.href)}
				<a href={link.href}>{link.label}</a>
			{/each}
			<a href="tel:09531606008" class="btn btn-primary phone-btn">📞 0953 160 6008</a>
		</nav>

		<button
			class="burger"
			aria-label="Toggle menu"
			aria-expanded={menuOpen}
			onclick={() => (menuOpen = !menuOpen)}
		>
			<span></span>
			<span></span>
			<span></span>
		</button>
	</div>

	{#if menuOpen}
		<nav class="mobile-nav">
			{#each links as link (link.href)}
				<a href={link.href} onclick={closeMenu}>{link.label}</a>
			{/each}
			<a href="tel:09531606008" class="btn btn-primary" onclick={closeMenu}>
				📞 0953 160 6008
			</a>
		</nav>
	{/if}
</header>

<style>
	header {
		position: sticky;
		top: 0;
		z-index: 100;
		background: transparent;
		transition:
			background 0.3s ease,
			box-shadow 0.3s ease;
	}

	header.scrolled {
		background: rgba(14, 14, 14, 0.92);
		backdrop-filter: blur(10px);
		box-shadow: 0 6px 20px rgba(0, 0, 0, 0.4);
	}

	.bar {
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding-top: 0.85rem;
		padding-bottom: 0.85rem;
	}

	.brand img {
		height: 48px;
		width: auto;
	}

	.desktop-nav {
		display: none;
		align-items: center;
		gap: 2rem;
	}

	.desktop-nav a {
		text-decoration: none;
		font-weight: 600;
		font-size: 0.95rem;
		color: var(--color-white);
		transition: color 0.2s ease;
	}

	.desktop-nav a:hover {
		color: var(--color-yellow);
	}

	.phone-btn {
		padding: 0.55rem 1.2rem;
		font-size: 0.85rem;
	}

	.burger {
		display: flex;
		flex-direction: column;
		gap: 5px;
		background: transparent;
		border: none;
		padding: 0.4rem;
	}

	.burger span {
		width: 26px;
		height: 3px;
		background: var(--color-yellow);
		border-radius: 3px;
	}

	.mobile-nav {
		display: flex;
		flex-direction: column;
		gap: 1rem;
		padding: 1rem 1.5rem 1.5rem;
		background: rgba(14, 14, 14, 0.98);
		border-top: 1px solid rgba(245, 197, 24, 0.2);
	}

	.mobile-nav a {
		text-decoration: none;
		color: var(--color-white);
		font-weight: 600;
	}

	@media (min-width: 860px) {
		.desktop-nav {
			display: flex;
		}
		.burger {
			display: none;
		}
	}
</style>
