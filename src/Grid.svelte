<script>
    import { cards } from './store.js';
	import Card from './Card.svelte';

</script>

<div class="grid">
    {#if $cards.length}
    <div class="inventory">
        Inventory
    </div>
    {/if}

    {#each $cards as card}
        <Card {...card}/>
    {/each}
</div>

<style>
    .grid {
        display: flex;
        justify-content: center;
        margin: 6vh 0.5vw;
        flex-wrap: wrap;
        row-gap: 10vh;
        column-gap: 6vw;
    }

    .inventory {
        width: 100%;
        font-size: 2em;
        font-variant: small-caps;
        font-weight: bold;
    }
</style>