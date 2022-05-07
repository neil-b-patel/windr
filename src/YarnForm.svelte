<script>
    import { cards } from './store.js';
    let image, imgInput;

    const onImageSelect = (e) => { 
        let file = e.target.files[0];
        let reader = new FileReader();
        reader.readAsDataURL(file);
        reader.onload = (e) => {
            image = e.target.result;
        };
    }
    const onSubmit = (e) => {
        const formData = new FormData(e.target);
        const data = {};
        for (let field of formData) {
            console.log(field);
            const [key, val] = field;
            data[key] = val;
        }
        if (!data["image"].size) {
            data["image"] = null;
        }
        else {
            data["image"] = image;
        }
        if (!data["inUse"]) {
            data["inUse"] = 0;
        }
        $cards = [...$cards, data]
    }
</script>

<form class="yarnForm" on:submit|preventDefault={onSubmit}>
    <div class="imgField">
        <label for="image" class="imageField">Image</label>
            {#if image}
                <div class="preview">
                    <img src={image} alt="yarn" />
                </div>
            {/if}
        <div class="imgUpload">
            <img 
                src="https://static.thenounproject.com/png/625182-200.png" 
                class="upload"
                alt="upload" 
                on:click={() => {imgInput.click();}} />
            <input 
                type="file"
                id="image"
                name="image"
                accept="image/*"
                on:change={onImageSelect}
                bind:this={imgInput} />
        </div>
    </div>
    <div class="fields">
        <div>
            <label for="name" class="nameField">Name</label>
            <input 
                type="text"
                id="name"
                name="name"
                value=""
                required
            />
        </div>
    
        <div>
            <label for="count">Count</label>
            <input 
                type="number"
                id="count"
                name="count"
                value=0
                min=0
                max=99
                required
            />
        </div>
    
        <div>
            <label for="material">Material</label>
            <input 
                type="text"
                id="material"
                name="material"
                value=""
                required
            />
        </div>
    
        <div>
            <label for="color">Color</label>
            <input 
                type="color"
                id="color"
                name="color"
                value=""
            />
        </div>

        <div>
            <label for="yardage">Yardage</label>
            <input 
                type="number"
                id="yardage"
                name="yardage"
                value=0
                min=0
                max=9999
                required
            />
        </div>
    
        <div>
            <label for="inUse">In Use?</label>
            <input 
                type="checkbox"
                id="inUse"
                name="inUse"
                value=1
            />
        </div>
    </div>

    <div>
        <button type="submit"> Wind it! </button>
    </div>
</form>

<style>
    .yarnForm {
        display: flex;
        flex-direction: column;
        align-items: flex-end;
        font-size: 1.25em;
        margin: 4vh 6vw;
        padding: 2rem 4rem;
        border: 0.1rem dotted lightgrey;
    }
    .fields {
        display: grid;
        grid-template-columns: max-content max-content;
        gap: 2vh 10vw;
    }
    .imgField {
        margin: 0 auto;
        margin-bottom: 1rem;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .upload {
        width: 25%;
        height: 25%;
        margin-top: 0.5rem;
        margin-bottom: 2rem;
    }
    .upload:hover {
        cursor: pointer;
    }
    .imgUpload {
        width: 20vw;
    }
    .preview {
        width: 150px;
        height: 150px;
        margin-top: 2rem;
        margin-bottom: 1rem;
    }
    img {
        height: 100%;
        width: 100%;
        object-fit:cover;
    }
    input {
        padding: 3vh 1vw;
        text-align: center;
        margin-bottom: 5vh;
    }
    label {
        font-size: 1em;
        font-weight: bold;
        font-variant: small-caps;
        text-align: center;
        margin-bottom: 1vh;
    }
    input[type=file] {
        display: none;
    }
    input[type=text] {
        height: 1.25em;
    }
    input[type=number] {
        height: 1.25em;
        width: max-content;
    }
    input[type=color] {
        font-size: 2em;
    }
    input[type=checkbox] {
        position: relative;
        top: 0.15rem;
        height: 35%;
        width: 35%;
    }
    input:focus {
        border: 0.5px solid black;
    }
    button[type=submit] {
        background-color: inherit;
        border-width: 0.1rem;
        border-radius: 2rem;
        padding: 0.5rem 1rem;
        font-variant: small-caps;
        font-weight: 500;
    }
    button[type=submit]:hover {
        background-color: whitesmoke;
    }
</style>