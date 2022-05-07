<script>
    import {cards} from './store.js';
    export let image;
    export let name;
    export let count;
    export let material;
    export let color;
    export let yardage;
    export let inUse;

    const deleteCard = (e) => {
        $cards = $cards.slice(0, -1);
    }

    const changeCount = (amt) => {
        amt = Number(amt);
        if (0 <= Number(count) + amt && Number(count) + amt <= 99) {
            $cards.forEach(card => {
                if (card["name"] === name 
                    && card["count"] === count
                    && card["material"] === material
                    && card["color"] === color
                    && card["inUse"] === inUse) 
                {
                    card["count"] = Number(card["count"]) + amt;
                    $cards = $cards;
                }
             });
        }
    }
</script>

<div>
    <div class="delete" on:click={deleteCard}/>
    <div class="card">
        {#if image}
            <div class="image">
                <img src={image} alt="image of {name}">
            </div>
        {/if}
        <div class="detail">
            <span class="label">Name: </span> 
            <span class="data"> {name} </span>
        </div>
        <div class="detail">
            <span class="label">Count: </span> 
            <span class="data"> {count} </span>
        </div>
        <div class="detail">
            <span class="label">Material: </span> 
            <span class="data"> {material} </span>
        </div>
        <div class="detail">
            <span class="label">Color: </span> 
            <span class="data">
                <div class="color" style="background-color:{color}" />
            </span>
        </div>
        <div class="detail">
            <span class="label">Yardage: </span> 
            <span class="data"> {yardage} </span>
        </div>
        <div class="detail">
            <span class="label">In Use: </span> 
            <span class="data"> {inUse ? "Yes" : "No"} </span>
        </div>
    </div>    
    <div class="countChange">
        <div class="decrease" on:click={() => {changeCount(-1);}}/>
        <div class="increase" on:click={() => {changeCount(1);}}/>
    </div>
</div>

<style>
    .card {
        font-size: 1.5em;
        line-height: 1.5em;
        padding: 3vh 5vw;
        border: 0.3rem double lightgrey;
        border-style: double;
        border-radius: 1rem;
        padding-bottom: 9vh;
    }
    .delete { 
        position: relative;
        top: 1.75rem;
        right: 0.5rem;
        height: 2rem;
        width: 2rem;
        background-color: lightgrey;
        border-radius: 0.5rem;
    }
    .delete::after {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        content: "\d7";
        font-size: 1.5em;
        color: white;
        text-align: center;
    }
    .countChange {
        display: flex;
        justify-content: space-between;
    }
    .decrease { 
        position: relative;
        bottom: 1.5rem;
        right: 0.5rem;
        height: 2rem;
        width: 2rem;
        background-color: lightcoral;
        border-radius: 0.5rem;
    }
    .decrease::after {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        content: "\2212";
        font-size: 1.3em;
        font-weight: bold;
        color: white;
        text-align: center;
    }
    .increase { 
        position: relative;
        bottom: 1.5rem;
        left: 0.5rem;
        height: 2rem;
        width: 2rem;
        background-color: lightgreen;
        border-radius: 0.5rem;
    }
    .increase::after {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        content: "\002B";
        font-size: 1.5em;
        color: white;
        text-align: center;
    }
    .delete:hover, .decrease:hover, .increase:hover {
        cursor: pointer;
    }
    .image {
        height: 150px;
        width: 150px;
        margin-bottom: 1rem;
        padding-top: 1rem;
        padding-bottom: 0.5rem;
    }
    .detail {
        font-size: 0.75em;
        display: list-item;
    }
    .label {
        float: left;
        text-align: left;
        font-weight: bold;
    }
    .data {
        float: right;
    }
    .color {
        display: inline-block;
        vertical-align: middle;
        height: 3vh;
        width: 4vw;
    }
    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
</style>