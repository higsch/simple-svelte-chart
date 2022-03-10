<script>
	import data from './data';

	import Chart from './components/Chart.svelte';
	import Selector from './components/Selector.svelte';

	let selectedOption = 'a';

	$: selectedData = data[selectedOption];
</script>

<div class="wrapper">
	<Chart />
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
