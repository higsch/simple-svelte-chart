<script>
    import { scaleLinear } from 'd3';

    import XAxis from './XAxis.svelte';
    import YAxis from './YAxis.svelte';
    import Datapoint from './Datapoint.svelte';
    import Line from './Line.svelte';

    export let data;
    export let xRange;
    export let yRange;

    const padding = 50;

    let width;
    let height;

    $: xScale = scaleLinear()
        .domain(xRange)
        .range([padding, width - padding]);

    $: yScale = scaleLinear()
        .domain(yRange)
        .range([height - padding, padding]);

    $: renderedData = data.map((d) => {
        return {
            x: xScale(d.x),
            y: yScale(d.y)
        };
    });
</script>

<div class="chart" bind:clientWidth={width} bind:clientHeight={height}>
    {#if (width && height)}
        <svg
            width={width}
            height={height}
        >
            <XAxis
                scale={xScale}
                y={height - padding}
            />
            <YAxis
                scale={yScale}
                x={padding}
            />
            <Line
                data={renderedData}
            />
            {#each renderedData as { x, y }}
                <Datapoint
                    x={x}
                    y={y}
                />
            {/each}
        </svg>
    {/if}
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
