<script>
	let videoFailed = $state(false);
</script>

<section id="top" class="jumbotron">
	<video
		autoplay
		muted
		loop
		playsinline
		poster="/images/team.jpg"
		src="/v.mp4"
		onerror={() => (videoFailed = true)}
		class:hidden={videoFailed}
	>
	</video>

	{#if videoFailed}
		<img src="/images/team.jpg" alt="Tamari's dining room" class="fallback-img" />
	{/if}

	<div class="overlay"></div>

	<div class="container content">
		<img src="/images/logo.png" alt="Tamari's" class="hero-logo" />
		<span class="eyebrow">Steak &amp; Seafood Restobar</span>
		<h1>Grilled to Perfection.<br />Served with Soul.</h1>
		<p>
			From jumbo T-bone steaks to fresh Cajun seafood boils — Tamari's brings BF Resort Village
			the flavors worth gathering for.
		</p>
		<div class="cta-row">
			<a href="#menu" class="btn btn-primary">View Our Menu</a>
			<a href="#contact" class="btn btn-outline">Book a Table</a>
		</div>
	</div>
</section>

<style>
	.jumbotron {
		position: relative;
		min-height: 92vh;
		display: flex;
		align-items: center;
		overflow: hidden;
		background: var(--color-black);
	}

	video,
	.fallback-img {
		position: absolute;
		inset: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	video.hidden {
		display: none;
	}

	.overlay {
		position: absolute;
		inset: 0;
		background: linear-gradient(
			180deg,
			rgba(14, 14, 14, 0.75) 0%,
			rgba(14, 14, 14, 0.55) 45%,
			rgba(14, 14, 14, 0.92) 100%
		);
	}

	.content {
		position: relative;
		z-index: 2;
		max-width: 760px;
		padding-top: 6rem;
		padding-bottom: 6rem;
	}

	.hero-logo {
		height: 70px;
		margin-bottom: 1.25rem;
	}

	h1 {
		font-size: clamp(2.2rem, 5.5vw, 3.6rem);
		color: var(--color-white);
	}

	h1 br {
		display: block;
	}

	.content p {
		color: var(--color-muted);
		font-size: 1.05rem;
		max-width: 560px;
	}

	.cta-row {
		display: flex;
		flex-wrap: wrap;
		gap: 1rem;
		margin-top: 1.5rem;
	}
</style>
