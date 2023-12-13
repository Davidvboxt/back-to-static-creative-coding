<script>
	import Navbar from '$lib/molecules/navigation.svelte';
	import SearchBar from '$lib/molecules/searchbar.svelte';
	import WishOverview from '$lib/molecules/wishoverview.svelte';
	import LayoutView from '$lib/molecules/layoutview.svelte';
	import { onMount } from 'svelte';

	export let data;

	let searchInput = null;
	let filteredWishes = data.wishes;

	function searchWishes(event) {
		event.preventDefault();
		const searchTerm = searchInput.value.toLowerCase();

		// Filter de wensen op basis van de zoekterm
		filteredWishes = data.wishes.filter((wish) => wish.heading.toLowerCase().includes(searchTerm));

		// Je kunt hier ook andere logica toevoegen voor het tonen/verbergen van de resultaten
	}

	onMount(() => {
		searchInput = document.getElementById('search-wishes');

		// Voeg submit event listener toe voor het tonen van resultaten bij het indienen van het formulier
		searchInput.form.addEventListener('submit', searchWishes);

		return () => {
			// Verwijder event listeners bij het opruimen van de component
			searchInput.form.removeEventListener('submit', searchWishes);
		};

		document.querySelector('.risoprint-container').addEventListener('mousemove', (event) => {
			// Add interactive effects like color change or movement on hover
		});
	});
</script>

<Navbar />

<main>
	<div class="risoprint-container">
		<div class="layer flower-background"></div>
		<!-- Other layers -->
		<div class="layer base-layer"><h1>Alle Wensen</h1></div>
		<div class="layer color-layer1"></div>
		<div class="layer color-layer2"></div>
		<!-- More layers as needed -->
	</div>

	<LayoutView {filteredWishes} {searchInput} {searchWishes} />

	<section id="custom-view" class="grid-overview wishes">
		<article>
			{#each filteredWishes as wish}
				<WishOverview {wish} {filteredWishes} />
			{/each}
		</article>
	</section>
</main>

<style>
	/* Magical risoprint animation */
	.risoprint-container {
		position: relative;
		height: 200px;
		margin-top: 30px;
		margin-bottom: 30px;
	}

	.layer {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}

	.flower-background {
		background-image: url('https://is1-ssl.mzstatic.com/image/thumb/Music116/v4/c4/71/9a/c4719a88-b80d-87b6-3c37-1308f8c9c3ef/artwork.jpg/592x592bf.webp'); /* Add your flower image here */
		background-size: cover;
		opacity: 0.6; /* Adjust for desired visibility */
		z-index: 3; /* Ensure it's below other layers */
	}

	.base-layer {
		/* ... */
		z-index: 3;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.color-layer1 {
		/* ... */
		z-index: 3;
	}

	.color-layer2 {
		/* ... */
		z-index: 4;
	}

	/* Continue with other layers and keyframe animations as previously defined */
	.risoprint-container {
		position: relative;
		width: 100%;
		height: 200px;
	}

	.layer {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}

	.base-layer {
		background-color: #f0e4d7; /* Base color */
	}

	.color-layer1 {
		background-color: rgba(255, 0, 0, 0.5); /* Semi-transparent red */
		transform: translate(2px, 2px); /* Slight misalignment */
		animation: magicEffect 5s infinite;
	}

	.color-layer2 {
		background-color: rgba(0, 0, 255, 0.5); /* Semi-transparent blue */
		transform: translate(-2px, -2px); /* Slight misalignment */
	}

	@keyframes magicEffect {
		0%,
		100% {
			opacity: 1;
		}
		50% {
			opacity: 0.5;
		}
	}

	main {
		width: fit-content;
		height: 100%;
		margin: auto;
		padding: var(--unit-default);
		background-color: var(--color-accent-75);
	}

	article {
		display: grid;
		grid-template-columns: 1fr;
		margin: auto;
	}

	@media (min-width: 42rem) {
		.grid-overview article {
			width: fit-content;
			grid-template-columns: 1fr 1fr;
		}
	}

	@media (min-width: 64rem) {
		.grid-overview article {
			width: fit-content;
			grid-template-columns: 1fr 1fr 1fr;
		}
	}

	@media (min-width: 42rem) {
		.grid-overview article {
			grid-template-columns: 1fr 1fr;
		}
	}

	@media (min-width: 64rem) {
		.grid-overview article {
			width: fit-content;
			grid-template-columns: 1fr 1fr 1fr;
		}
	}

	@keyframes fade-in {
		from {
			opacity: 0;
			transform: translateY(
				var(--unit-default)
			); /* Optioneel: voeg een lichte verticale verschuiving toe */
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}
</style>
