<script>
	let options = [
		{
			name: "Rental skis",
			price: 150,
			onSale: true,
		},
		{
			name: "Chalet access",
			price: 250,
			onSale: true,
		},
		{
			name: "Lessons",
			price: 175,
			onSale: false,
		},
	];
</script>

<main>
	<h1>Alpine Ski House</h1>
	<h2>There are {options.length} options available</h2>
	<!--TODO: Add code to display options-->
	{#each options as option}
		<div class="row">
			<div>
				{option.name}
			</div>
			<div>
				<!--TODO: Add sale display-->
				{#if option.onSale}
					On sale!
				{:else}
					Order soon!
				{/if}
			</div>
			<div>
				§{option.price}
			</div>
		</div>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	.row {
		display: grid;
		grid-template-columns: 1fr 1fr 1fr;
		margin: 0.1em;
		font-size: 1.4em;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
