<script>
    import { onMount } from 'svelte';

    let score = 0;
    export let playerName = "enter name";
    let pointsEffect = false;

    //SET AND GET SCORE
    onMount(() => {
        if(playerName === "Begotten Son") {
            score = localStorage.getItem('player1') ? localStorage.getItem('player1') : localStorage.player1 = 0;
        } 
        if(playerName === "AhkoteeKia") {
            score = localStorage.getItem('player2') ? localStorage.getItem('player2') : localStorage.player2 = 0;
        }     
    });

    //ADD SCORE
    function addScore(num) {
        if(playerName === "Begotten Son") {
            localStorage.player1 = Number(localStorage.player1) + num;
            score = Number(score) + num;
            animateScore();
        }else{
            localStorage.player2 = Number(localStorage.player2) + num;
            score = Number(score) + num;
            animateScore();
        };
    }
    function add100() {
        addScore(100);
    }
    function add200() {
        addScore(200);
    }
    function add300() {
        addScore(300);
    }
    function reset() {
        score = 0;
        localStorage.player1 = 0;
        localStorage.player2 = 0;
    }
    
    //SCORE ANIMATION
    function animateScore() {
        pointsEffect = true;
        setTimeout(() => {
            pointsEffect = false;
        }, 500);
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

    .score {
        transition: 400ms ease-out;
    }

    .pointsEffect {
        color: gold;
        transform: scale(1.2);
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
        <button class="points button"  on:click={add100}>Noun</button>
        <button class="points button" on:click={add200}>Adjective</button>
        <button class="points button" on:click={add300}>Adverb</button>
        <button class="reset button" on:click={reset}>reset</button>
    </section>
    <section class="player-card">
        <h2>{playerName}</h2>
        <h2 class:pointsEffect class="score">{score}</h2>
        <div class="profile">
            <slot>{playerName}'s picture</slot>
        </div>
    </section>  
</main>
