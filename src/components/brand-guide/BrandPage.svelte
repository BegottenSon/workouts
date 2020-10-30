<script>
    import { createEventDispatcher } from 'svelte';
    
    export let pageTitle = "" || "Text Title";
    export let pageNumber = '' || "#";
    export let paraOne, paraTwo, paraThree = '';
    export let src = "";

    const dispatch = createEventDispatcher();

    function turnPage() {
        dispatch('pageTurn', {
            page: 2
        })
    }
</script>
<section>
    <img class="index-icon" on:click={turnPage} src="https://res.cloudinary.com/begottenson/image/upload/c_scale,w_300/v1601428948/Begotten%20Sounds/Begotten_Sounds_Icon.png" alt="Begotten Sounds Icon">
    <h2 class="side-index">{pageTitle}</h2>
    <h2 class="index-number">{pageNumber}</h2>
    <b/>
    <div class="text-section">
        <h1>{pageTitle}</h1>
        <p>{paraOne}</p>
        <p>{paraTwo}</p>
        <p>{paraThree}</p>
    </div>
    <div class="show-section">
        <img src={src} on:click={turnPage} alt="Begotten Sounds Logo">
    </div>
</section>

<style>
    
    section {
        --red: #e91b50;
        --dark: #1a1a1a;
        --white: #ebebeb;
        display: grid;
        grid-template-columns: min-content repeat(3, 1fr);
        grid-template-rows: min-content 2fr min-content;
        background-color: var(--white);
        /* height: 60vh; */
        margin: 1em 0;
    }

    .index-icon {
        height: 2.5em;
        grid-row: 1;
        grid-column: 1;
    }

    .side-index {
        font-size: 0.9em;
        color: var(--red);
        writing-mode: sideways-lr;
        align-self: flex-end;
        border-bottom: 2px solid var(--red);
        grid-row: 2;
        grid-column: 1;
        padding-bottom: 1em;
        margin: 0.8em;
    }

    .index-number {
        font-size: 0.9em;
        color: var(--red);
        align-self: center;
        justify-self: center;
        grid-row: 3;
        grid-column: 1;
        margin: 0.8em;
    }

    b {
        border-right: 2px solid var(--red);
        grid-row: 1/4;
        grid-column: 1;
    }

    h1 {
        text-align: center;
        font-weight: bold;
        color: var(--dark);
    }

    p {
        font-size: 0.67em;
        color: var(--dark);
        padding: 0 1em;
    }

    .text-section {
        grid-row: 2;
        grid-column: 2;
        border: 2px solid var(--red);
        margin: 0 1em;
    }

    .show-section {
        display: flex;
        justify-content: center;
        grid-row: 2;
        grid-column: 3/5;
        background-color: var(--dark);
        border: 2px solid var(--red);
        margin-right: 1em;
    }

    img {
        align-self: center;
        justify-self: center;
        cursor: pointer;
    }
</style>