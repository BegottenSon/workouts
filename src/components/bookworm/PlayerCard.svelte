<script>
    import { onMount } from 'svelte';

    onMount(() => {
        // if(localStorage.player1) {
        //     localStorage.player1 = localStorage.player1;
        //     localStorage.player2 = localStorage.player2;
        // }else{
        //     localStorage.player1 = 0;
        //     localStorage.player2 = 0;
        // }
        localStorage.getItem('player1') ? localStorage.getItem('player1') : localStorage.player1 = 0;
        localStorage.getItem('player2') ? localStorage.getItem('player2') : localStorage.player2 = 0;        
    });
    export let score = 0;
    export let playerName = "enter name";
    let playerOne = localStorage.player1;
    let playerTwo = localStorage.player2;
    

    function add100() {
        if(playerName === "Begotten Son") {
            playerOne = Number(playerOne) + 100;
            score = playerOne;
        }else{
            playerTwo = Number(playerTwo) + 100;
            score = playerTwo;
        }
    }
    function add200() {
        if(playerName === "Begotten Son") {
            playerOne = Number(playerOne) + 200;
            score = playerOne;
        }else{
            playerTwo = Number(playerTwo) + 200;
            score = playerTwo;
        }
    }
    function add300() {
        if(playerName === "Begotten Son") {
            playerOne = Number(playerOne) + 300;
            score = playerOne;
        }else{
            playerTwo = Number(playerTwo) + 300;
            score = playerTwo;
        }
    }
    function reset() {
        score = 0;
        playerOne = 0;
        playerTwo = 0;
    }
</script>
<style>
    main {
        background-color: thistle;
        border-radius: 4px;
    }

    .profile {
        margin: 0;
    }

    .button {
        appearance: none;
        border: 1px outset rgb(199, 62, 188);
        border-radius: 2px;
        color: var(--text-color);
        cursor: pointer;
        font-size: 14px;
        margin-top: 1em;
    }

    .points {
        background-color: var(--secondary-color);
        font-weight: bold;
        font-size: 10px;
    }

    .reset {
        background-color: rgb(141, 44, 52);
        color: rgb(228, 107, 147);
        padding: 0.05em 0.5em;
    }

    .button:active {
        border-style: inset;
    }
</style>
<main>
    <section>
        <button class="points button" on:click={add100}>Noun</button>
        <button class="points button" on:click={add200}>Adjective</button>
        <button class="points button" on:click={add300}>adverb</button>
        <button class="reset button" on:click={reset}>reset</button>
    </section>
    <section class="player-card">
        <h2>{playerName}</h2>
        <h2>{score}</h2>
        <div class="profile">
            <slot>{playerName}'s picture</slot>
        </div>
    </section>  
</main>
