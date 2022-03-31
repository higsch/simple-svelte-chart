<script>
	import data from './data';

	import Chart from './components/Chart.svelte';
	import Selector from './components/Selector.svelte';

	let selectedOption = 'a';

	$: selectedData = data[selectedOption].sort((a, b) => a.x < b.x ? 1 : -1);
</script>

<div class="wrapper">
	<Chart 
		data={selectedData}
		xRange={[0, 20]}
		yRange={[0, 16]}
	/>
	<Selector
		options={Object.keys(data)}
		bind:selected={selectedOption}
	/>
</div>

<style>
	.wrapper {
		display: flex;
		flex-direction: column;
		width: 100%;
		height: 100%;
	}
</style>
