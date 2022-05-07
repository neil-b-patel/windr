<script>
    export let image;
    export let name;
    export let count;
    export let material;
    export let color;
    export let inUse;
</script>

<div class="card">
    <div class="image">
        <img src={image} alt="image of {name}">
    </div>
    <div class="detail">
        <b class="label">Name: </b> {name}
    </div>
    <div class="detail">
        <b class="label">Count: </b> {count}
    </div>
    <div class="detail">
        <b class="label">Material: </b> {material}
    </div>
    <div class="detail">
        <b class="label">Color: </b> <div class="color" style="background-color:{color}"></div>
    </div>
    <div class="detail">
        <b class="label">In Use?: </b> {inUse ? "Yes" : "No"}
    </div>
</div>

<style>
    .card {
        /* min-width: 33%; */
        /* max-width: 100%; */
        font-size: 1.5em;
        line-height: 1.5em;
        /* margin: 4vh 6vw; */
        padding: 3vh 6vw;
        border: 0.3rem double lightgrey;
        border-style: double;
        border-radius: 1rem;
    }
    .detail {
        font-size: 0.75em;
        text-align: center;
    }
    .label {
        display: block;
        text-align: left;
    }
    .color {
        display: inline-block;
        vertical-align: middle;
        height: 3vw;
        width: 6vw;
    }
</style>