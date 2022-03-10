<script>
    import { scaleLinear } from 'd3';

    const padding = 50;

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
    />
</div>

<style>
    .chart {
        flex: 1;
        width: 100%;
        overflow: hidden;
    }
</style>
