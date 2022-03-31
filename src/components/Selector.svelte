<script>
    export let options = [];
    export let selected;
</script>

<div class="selector">
    {#each options as option}
        <span>
            <input
                type="radio"
                id={option}
                on:change={() => (selected = option)}
                checked={selected === option}
            />
            <label for={option}>{option}</label>
        </span>
    {/each}
</div>

<style>
    .selector {
        display: flex;
        justify-content: center;
        gap: 16px;
        width: 100%;
        height: 100px;
        font-size: 20px;
    }
</style>
