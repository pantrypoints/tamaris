<script>
	import Jumbotron from '$lib/components/Jumbotron.svelte';
	import Promo from '$lib/components/Promo.svelte';
	import DishCarousel from '$lib/components/DishCarousel.svelte';
	import FacebookCTA from '$lib/components/FacebookCTA.svelte';
	import ContactForm from '$lib/components/ContactForm.svelte';
</script>

<svelte:head>
	<title>Tamari's Steak and Seafood Restobar</title>
	<meta
		name="description"
		content="Tamari's Steak and Seafood Restobar in BF Resort Village, Las Piñas City. Jumbo T-bone steaks, Cajun seafood boils, and grilled favorites."
	/>
</svelte:head>

<Jumbotron />
<Promo />
<DishCarousel />
<FacebookCTA />
<ContactForm />
