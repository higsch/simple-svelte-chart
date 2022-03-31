<script>
    export let scale;
    export let x;

    const textOffset = 10;

    $: y0 = scale.range()[1];
    $: y1 = scale.range()[0];

    $: ticks = scale.ticks();
</script>

<g class="axis">
    <line x1={x} y1={y0} x2={x} y2={y1} />
    <g class="ticks">
        {#each ticks as tick}
            <g
                class="tick"
                transform="translate({x - textOffset} {scale(tick)})"
            >
                <text dy={textOffset}>
                    {tick}
                </text>
            </g>
        {/each}
    </g>
</g>

<style>
    line {
        stroke: gray;
        stroke-width: 2;
        stroke-linecap: round;
    }

    text {
        fill: gray;
        text-anchor: end;
        font-size: 20px;
    }
</style>
