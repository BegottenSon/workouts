<script>
    import { createEventDispatcher } from 'svelte';
    import { flip } from 'svelte/animate';
    import { quintOut } from 'svelte/easing';

    const dispatch = createEventDispatcher();

    function turnPage() {
        dispatch('pageTurn', {
            page: 1
        })
    }
</script>

<main class="cover" >
    <h2 class="side-tab">BEGOTTEN SOUNDS BRAND</h2>
    <b class="intro-b"/>
    <img class="icon" on:click={turnPage} src="https://res.cloudinary.com/begottenson/image/upload/c_scale,w_300/v1601428948/Begotten%20Sounds/Begotten_Sounds_Icon.png" alt="Begotten Sounds Icon">
    <h3 class="title">BEGOTTEN SOUNDS</h3>
</main>

<style>
    @import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700;900&display=swap");
   
   main {
       --red: #e91b50;
       --dark: #1a1a1a;
       --white: #ebebeb;
       display: grid;
       grid-template-columns: min-content 1fr;
       grid-template-rows: 1fr;
       height: 60vh;
       background-color: var(--dark);
       color: var(--white);
       font-family: 'Roboto';
   }

   .side-tab {
       font-size: 0.9em;
       color: var(--red);
       writing-mode: sideways-lr;
       align-self: center;
       grid-row: 1;
       grid-column: 1;
       margin: 0.8em;
   }

   .intro-b {
       grid-row: 1;
       grid-column: 1;
       border-right: 2px solid var(--red);
   }

   .icon {
       grid-row: 1;
       grid-column: 2;
       place-self: center;
       align-self: center;
       justify-self: center;
       cursor: pointer;
   }

   .title {
       grid-row: 1;
       grid-column: 2;
       align-self: flex-end;
       justify-self: center;
   }

</style>