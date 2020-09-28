<script>
    export let name = " Toggle Tople"
</script>

<style>
    section {
        display: flex;
        flex-direction: column;
        height: 25vh;
        justify-content: space-between;
        align-items: center;
    }

    .toggle {
        height: 5em;
    }

    #toggle {
        display: none;
    }

    label {
        background-color: var(--purple);
        border: 0.5px solid var(--purple);
        width: 7em;
        height: 3em;
        display: inline-block;
        border-radius: 50px;
        position: relative;
        transition: 500ms cubic-bezier(0.85, 0, 0.5, 1);
        cursor: pointer;
        transform:  rotate(-45deg);
    }

    label:before {
        position: absolute;
        content: "";
        display: block;
        width: 2.3em;
        height: 2.3em;
        top: .25em;
        left: .25em;
        border-radius: 2em;
        border: 2px solid var(--gum);
        transition: 300ms 400ms cubic-bezier(0.95, -0.02, 0.71, 1);
    }

    #toggle:checked + label:before {
        background-color: var(--gum);
        left: 4.2em;
    }

    #toggle:checked + label {
        transform: rotate(45deg);
    }
</style>

<svelte:head><title>Toggle Tople</title></svelte:head>
<section>
    <h1> {name} </h1>
    <div class="toggle">
        <input type="checkbox" id="toggle">
        <label for="toggle"></label>
    </div>
</section>