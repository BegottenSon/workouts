<script>
    import { fly } from 'svelte/transition';
    import { cubicIn, elasticIn } from 'svelte/easing';
    export let name = " Toggle Friction";

    let checked = false;

    function toggle() {
        checked = !checked;
    }
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
        position: relative;
        height: 5em;
    }

    #toggleFriction {
        display: none;
    }

    #balls {
        background-color: var(--purple);
        border: 2px solid var(--purple);
        width: 2.3em;
        height: 2.3em;
        display: inline-block;
        border-radius: 2em;
        position: relative;
        transition: 500ms cubic-bezier(0.85, 0, 0.5, 1);
        cursor: pointer;
    }

    #balls:before {
        position: absolute;
        content: "";
        display: block;
        width: 2.3em;
        height: 2.3em;
        top: -0.1em;
        left: -5em;
        border-radius: 2em;
        border: 2px solid var(--gum);
        background-color: var(--gum);
        transition: 300ms cubic-bezier(0.95, -0.02, 0.71, 1);
    }

    #balls:after {
        position: absolute;
        content: "";
        display: block;
        width: 2.3em;
        height: 2.3em;
        top: -0.1em;
        transform: translateX(2.5em);
        border-radius: 2em;
        border: 2px solid var(--gum);
        background-color: var(--gum);
        transition: 300ms cubic-bezier(0.95, -0.02, 0.71, 1);
    }

    #leftString {
        position: absolute;
        /* transform: translateX(-3.6em); */
        top: -2.9em;
        width: 0.12em;
        height: 3em;
        background-color: rgb(229, 198, 240);
        transition: 300ms cubic-bezier(0.95, -0.02, 0.71, 1);
    }

    #toggleFriction:checked + #balls:before {
        left: -2.7em;
    }

    #toggleFriction:checked + #balls:after {
        left: 5em;
    }

    #toggleFriction:checked + #balls {
    }
</style>

<section>
    <h1> {name} </h1>
    <div class="toggle">
        {#if checked}
        <div id="leftString" transition:fly="{{x: 100, easing: elasticIn}}"></div>   
        {/if}
        
        <label for="toggleFriction" id="balls">
         <input type="checkbox" bind:checked id="toggleFriction">   
        </label>
    </div>
</section>