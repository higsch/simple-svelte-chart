<script>
    import { tweened } from 'svelte/motion';
    import { cubicOut } from 'svelte/easing';

    export let x;
    export let y;

    const tX = tweened(null, { duration: 400, easing: cubicOut });
    const tY = tweened(null, { duration: 400, easing: cubicOut });

    $: tX.set(x);
    $: tY.set(y);
</script>

<g transform="translate({$tX} {$tY})">
    <circle cx="0" cy="0" r="10" />
</g>
