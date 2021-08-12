<script>
	function sleep() {
		return new Promise(res => setTimeout(res, 4000))
	}

	// TODO: Add loadData function
	async function loadData() {
		// await sleep();
		const response = await fetch("./data.json");
		const json = await response.json();
		return json.options;
	}
</script>

<main>
	<h1>Alpine Ski House</h1>
	<!--TODO: Add await block-->
	{#await loadData()}
		Loading data...
	{:then options}
		<h2>Select your options</h2>
		<h3>There are {options.length} options available</h3>
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

	{/await}
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
