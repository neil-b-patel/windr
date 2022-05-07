<script>
    import { cards } from './store.js';
	import Card from './Card.svelte';

    let newCard = {};

    
    // export const createCard = (data) => {
    //     Object.entries(data).forEach(([key, val]) => {
    //         console.log(key, val);
    //     })
    //     $cards.push(data);
    //     console.log($cards);
    // }
</script>

<div class="grid">
        {#each $cards as card}
            <Card {...card}/>
        {/each}
        <!-- <Card/>
        <Card/>
        <Card/>            

        <Card/>
        <Card/>
        <Card/>    

        <Card/>
        <Card/>
        <Card/> -->
</div>

<style>
    .grid {
        display: flex;
        justify-content: center;
        margin: 6vh 0.5vw;
        flex-wrap: wrap;
        row-gap: 10vh;
        column-gap: 8vw;
    }
</style>