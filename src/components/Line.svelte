<script>
    import { tweened } from "svelte/motion";
    import { cubicOut } from "svelte/easing";
    import { line, curveMonotoneX } from "d3";
    import { interpolatePath } from "d3-interpolate-path";

    export let data;

    const lineGenerator = line()
        .x(d => d.x)
        .y(d => d.y)
        .curve(curveMonotoneX);
    
    const tLinePath = tweened(null, {
        duration: 400,
        easing: cubicOut,
        interpolate: interpolatePath
    });
    
    $: linePath = lineGenerator(data);

    $: tLinePath.set(linePath);
</script>

<path
    class="line"
    d={$tLinePath}
/>

<style>
    .line {
        fill: none;
        stroke: purple;
        stroke-width: 2;
    }
</style>