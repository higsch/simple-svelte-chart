<script>
    import { scaleLinear } from 'd3';

    import Datapoint from './Datapoint.svelte';

    export let data;
    export let xRange;
    export let yRange;

    const padding = 50;

    $: xScale = scaleLinear()
        .domain(xRange)
        .range([padding, width - padding]);
    
    $: yScale = scaleLinear()
        .domain(yRange)
        .range([height - padding, padding]);

    $: renderedData = data.map(d => {
        return {
            x: xScale(d.x),
            y: yScale(d.y)
        };
    });

    let width;
    let height;
</script>

<div
    class="chart"
    bind:clientWidth={width}
    bind:clientHeight={height}
>
    <svg
        width={width}
        height={height}
    >
        <!-- <XAxis />
        <YAxis /> -->
        {#each renderedData as { x, y }}
            <Datapoint
                x={x}
                y={y}
            />
        {/each}
    </svg>
</div>

<style>
    .chart {
        flex: 1;
        width: 100%;
        overflow: hidden;
    }

    /* svg {
        background: red;
    } */
</style>
