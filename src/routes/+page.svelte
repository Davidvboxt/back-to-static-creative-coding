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
	<section class="primary-section">
		<h1>1</h1>
	</section>

	<LayoutView {filteredWishes} {searchInput} {searchWishes} />

	<section id="custom-view" class="grid-overview wishes">
		<article>
			{#each filteredWishes as wish}
				<WishOverview {wish} {filteredWishes} />
			{/each}
		</article>
	</section>

	<section class="primary-section">
		<h1>2</h1>
	</section>
	<div class="sub-header">
		<div class="risoprint-container block_1 hover-area">
			<div class="layer base-layer"><h2>Overizchtspagina</h2></div>
			<div class="layer color-layer1"></div>
			<div class="layer color-layer2"></div>
			<div class="hidden-object">
				<svg
					class="flower"
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 256 256"
					id="IconChangeColor"
					height="200"
					width="200"
					><rect width="256" height="256" fill="none"></rect><circle
						cx="128"
						cy="128"
						r="28"
						fill="none"
						stroke="#000"
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="8"
					></circle><path
						d="M115,103.2c-7.3-15.4-15-34.6-15-47.2a28,28,0,0,1,56,0c0,12.6-7.7,31.8-15,47.2"
						fill="#ffffff"
						stroke="#000"
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="8"
						id="mainIconPathAttribute"
					></path><path
						d="M100,126.8c-17-1.3-37.5-4.3-48.4-10.6a28,28,0,0,1,28-48.4C90.5,74,103.3,90.3,113,104.4"
						fill="#ffffff"
						stroke="#000"
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="8"
						id="mainIconPathAttribute"
					></path><path
						d="M113,151.6c-9.7,14.1-22.5,30.4-33.4,36.6a28,28,0,1,1-28-48.4c10.9-6.3,31.4-9.3,48.4-10.6"
						fill="#ffffff"
						stroke="#000"
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="8"
						id="mainIconPathAttribute"
					></path><path
						d="M141,152.8c7.3,15.4,15,34.6,15,47.2a28,28,0,0,1-56,0c0-12.6,7.7-31.8,15-47.2"
						fill="#ffffff"
						stroke="#000"
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="8"
						id="mainIconPathAttribute"
					></path><path
						d="M156,129.2c17,1.3,37.5,4.3,48.4,10.6a28,28,0,0,1-28,48.4c-10.9-6.2-23.7-22.5-33.4-36.6"
						fill="#ffffff"
						stroke="#000"
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="8"
						id="mainIconPathAttribute"
					></path><path
						d="M143,104.4c9.7-14.1,22.5-30.4,33.4-36.6a28,28,0,0,1,28,48.4c-10.9,6.3-31.4,9.3-48.4,10.6"
						fill="#ffffff"
						stroke="#000"
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="8"
						id="mainIconPathAttribute"
					></path></svg
				>
			</div>
		</div>
		<div class="risoprint-container block_2">
			<div class="layer base-layer"><h2>over</h2></div>
			<div class="layer color-layer1"></div>
			<div class="layer color-layer2"></div>
		</div>
		<div class="risoprint-container block_3">
			<div class="layer base-layer"><h1>Alle Wensen</h1></div>
			<div class="layer color-layer1"></div>
			<div class="layer color-layer2"></div>
		</div>
	</div>

	<LayoutView {filteredWishes} {searchInput} {searchWishes} />

	<section id="custom-view" class="grid-overview wishes">
		<article>
			{#each filteredWishes as wish}
				<WishOverview {wish} {filteredWishes} />
			{/each}
		</article>
	</section>

	<section class="primary-section">
		<h1>3</h1>
	</section>

	<section class="thunder">
		<div id="lightning-container">
			<h1 id="breathing-header">Alle Wensen</h1>
			<div class="rain"></div>
		</div>
	</section>

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
	/* Algemeen */

	.primary-section {
		margin-top: 100px;
		margin-bottom: 20px;
	}

	/* Magical risoprint animation 3 */
	.thunder {
		height: 300px;
		width: 100%;
		margin-top: 50px;
		margin-bottom: 50px;
		display: flex;
		justify-content: center;
		align-items: center;
		background-color: black;
		color: white;
		animation: thunder 0.3s linear infinite;
		
	}

	@keyframes thunder {
		0% {
			background-position: 0% 0%;
		}
		100% {
			background-position: 20% 100%;
		}
	}

	#breathing-header {
		font-size: 3rem;
		text-align: center;
		color: #00bfff; /* Deep Sky Blue */
		animation:
			glow 1.5s ease-in-out infinite alternate,
			breathe 3s ease-in-out infinite;
	}

	@keyframes glow {
		from {
			text-shadow:
				0 0 10px #00bfff,
				0 0 20px #00008b,
				0 0 30px #00008b,
				0 0 40px white; /* Sky Blue, Dark Blue, White */
		}
		to {
			text-shadow:
				0 0 5px white,
				0 0 15px #00008b,
				0 0 25px #00bfff,
				0 0 35px #00008b; /* White, Dark Blue, Sky Blue */
		}
	}

	@keyframes breathe {
		0%,
		100% {
			transform: scale(1);
		}
		50% {
			transform: scale(1.1);
		}
	}

	.rain::before {
		content: '';
		position: absolute;
		width: 100%;
		height: 100%;
		background-image: url('https://w7.pngwing.com/pngs/428/585/png-transparent-white-lightning-illustration-lightning-strike-lightning-blue-computer-wallpaper-desktop-wallpaper.png');
		/* top: -100px; */
		transform: rotate(180deg);
		animation: lightining 4s linear infinite;
		opacity: 1;
	}
	@keyframes lightining {
		0% {
			opacity: 0;
		}
		20% {
			opacity: 0;
		}
		21% {
			opacity: 1;
		}
		25% {
			opacity: 0;
		}
		30% {
			opacity: 0;
		}
		31% {
			opacity: 1;
		}
		35% {
			opacity: 0;
		}
		100% {
			opacity: 0;
		}
	}

	/* Magical risoprint animation 2 */

	.flower {
		position: absolute;
		left: 0;
		top: 5px;
		height: 50px;
	}

	.hover-area {
		/* Your styles for the hover area */
		width: 200px;
		height: 200px;
		border: 1px solid black;
		position: relative;
	}

	.hidden-object {
		/* Initially hide the object */
		display: none;
		position: absolute;
		top: 0;
		left: 0;
		opacity: 50;

		/* Styles for the object */
		background-color: lightblue;
		width: 100%;
		height: 100%;
		text-align: center;
		line-height: 200px; /* Example to center text vertically */
	}

	.hover-area:hover .hidden-object {
		/* Display the object when hover-area is hovered */
		display: block;
		animation: fadeIn 1s; /* Example animation */
	}

	@keyframes fadeIn {
		from {
			opacity: 0;
		}
		to {
			opacity: 5;
		}
	}

	.block_1 {
		position: relative;
		width: 100%;
		height: 65px;
	}
	.block_2 {
		position: relative;
		grid-column: auto/span 2;
		width: 100%;
		height: 65px;
	}
	.block_3 {
		position: relative;
		grid-column: auto/span 3;
		grid-row: auto/span 2;
		width: 100%;
		height: 100px;
	}
	.sub-header {
		display: grid;
		margin-top: 30px;
		margin-bottom: 30px;
		grid-gap: 10px;
		grid: auto-flow dense / 700px 60px 1fr;
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
		opacity: 0.6;
		z-index: 3;
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

	.color-layer1 {
		background-color: rgba(255, 0, 0, 0.5);
		transform: translate(2px, 2px);
		animation: magicEffect 5s infinite;
	}

	.color-layer2 {
		background-color: rgba(0, 0, 255, 0.5);
		transform: translate(-2px, -2px);
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
