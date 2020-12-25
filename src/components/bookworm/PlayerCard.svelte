<script>
    import { onMount } from 'svelte';
    import { fade } from 'svelte/transition';

    export let playerName = "enter name";
    let score = 0;
    let pointsEffect = false;
    let disable = false;
    let minute = 1000 * 60;
    let coolDownTime = minute * 30;
    let originalTime = 30 * 60;
    let timer = 30 * 60;

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
        runTimer();
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

    //TIMER FOR THE COOL DOWN DISABLE BUTTONS
    function theTimer() {
        localStorage.timer = timer;
            if(timer > 0) {
                timer -= 1
            }else{
                clearTimer()
                localStorage.removeItem("timer")
            }
    }
    
    function clearTimer() {
        clearInterval(runningTime);
        timer = originalTime;
        console.log("timer is cleared: " + timer);
    }

    function runTimer() {
        runningTime = setInterval(theTimer, 1000);
    }

    let runningTime;
    $: minutes = Math.floor(timer / 60);
    $: seconds = Math.floor(timer - minutes * 60);
    

</script>
<style>
    main {
        background-color: thistle;
        border-radius: 4px;
        box-shadow: 1px 2px 5px rgba(38, 2, 53, 0.418);
        margin: 0 0.5em;
        position: relative;
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
    }

    .player-card  h2:first-child {
        margin-top: 1.2em;
    }

    .cool-down-shield {
        background-color: var(--sky-blue);
        display: flex;
        align-items: center;
        justify-content: center;
        height: 100%;
        width: 100%;
        filter: opacity(0.8);
        text-align: center;
        position: absolute;
        top: 0;
        left: 0;
        animation: coolDown 108000s forwards;
    }

    .timer {
        background-color: var(--sky-blue);
        border-radius: 8px;
        filter: saturate(120);
        padding: 1em;
    }

    @keyframes coolDown {
        from {filter: opacity(0.8);}
        to {filter: opacity(0.3)}
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
    {#if disable}
        <div class="cool-down-shield" 
        transition:fade="{{delay: 800, duration: 300}}">
            <h2 class="timer">
                {minutes}:
                {#if seconds < 10}
                0{seconds}
                {:else}
                {seconds}
                {/if}
            </h2>
        </div>
    {/if}
</main>
