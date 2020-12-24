<script>
    import { onMount } from 'svelte';

    export let playerName = "enter name";
    let score = 0;
    let pointsEffect = false;
    let disable = false;
    let minute = 1000 * 60
    let coolDownTime = minute * 30;

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
        disableButtons();
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

    //DISABLE BUTTONS FOR LIMITED TIME
    function disableButtons() {
        disable = true;
        setTimeout(() => {
            disable = false;
        }, coolDownTime);
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
        box-shadow: 1px 2px 5px rgba(38, 2, 53, 0.418);
        margin: 0 0.5em;
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
        transition: 400ms ease-out;
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

    .points:disabled {
        background-color: rgb(108, 200, 253);
        color: rgb(0, 41, 165);
        animation: coolDown 108000s forwards;
    }

    .player-card  h2:first-child {
        margin-top: 1.2em;
    }

    @keyframes coolDown {
        from {filter: saturate(1);}
        to {filter: saturate(0.2);}
    }
</style>
<main class="player-container">
    <section>
        <button class="points button" on:click={add100} disabled={disable}>Noun</button>
        <button class="points button" on:click={add100} disabled={disable}>Verb</button>
        <button class="points button" on:click={add200} disabled={disable}>Adjective</button>
        <button class="points button" on:click={add300} disabled={disable}>Adverb</button>
        <br>
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
