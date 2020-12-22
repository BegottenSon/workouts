<script>
    import PlayerCard from "../components/bookworm/PlayerCard.svelte";
    import { onMount } from 'svelte';

    let theWord = "Add New Word";
    let playing = false;

    function playGame() {
        playing = true;
        localStorage.word = theWord;
        localStorage.playing = playing;
    }

    function newGame() {
        playing = false;
        localStorage.playing = playing;
        localStorage.removeItem("word");
        localStorage.player1 = 0;
        localStorage.player2 = 0;
        theWord = "";
    }

    onMount(()=> {
        theWord = localStorage.word;
        playing = JSON.parse(localStorage.playing);
    })
    
</script>

<style>

    .game-container {
        --secondary-color: rgb(136, 230, 164);
        --heading-color: rgb(158, 11, 146);
        --text-color: rgb(199, 62, 188);
        background-color: var(--secondary-color);
        color: var(--text-color);
        min-height: 100vh;
        min-height: -webkit-fill-available;
        width: 99vw;
        margin: 0;
        position: absolute;
        top: 0;
        left: 0;  
    }

    h1 {
        color: var(--heading-color);
        text-align: center;
    }

    .word-heading {
        display: flex;
        flex-direction: column;
        text-align: center;
    }

    .word-heading h2, .word-heading h3 {
        margin: 0;
    }
    .word-heading h2 {
        color: var(--heading-color);
    }

    .word-heading h3 {
        text-transform: uppercase;
        font-weight: bold;
        margin-bottom: 1em;
    }

    section {
        display: flex;
        /* gap: 1em; */
        justify-content: center;
        text-align: center;
    }

    img {
        width: 46vw;
    }

    button {
        appearance: none;
        background-color: rgb(73, 226, 119);
        border: 2px outset rgb(199, 62, 188);
        color: var(--text-color);
        cursor: pointer;
        margin-top: 1em;
        padding: 1em;
    }

    button:active {
        border-style: inset;
    }

    .play-btn {
        border-radius: 8px;
        padding: 0.5em;
    }

    input[type = "text"] {
        appearance: none;
        background: none;
        border: none;
        border-bottom: 4px solid var(--heading-color);
        color: var(--text-color);
        font-size: 14px;
    }

    @media (min-width: 600px) {
        main {
            width: 80vw;
            height: 100vh;
        }

        img {
            width: 28vw;
        }
    }
</style>

<main class="game-container">
    <h1>The Book Worm Game</h1>
    {#if !playing}
        <h4>Add word:</h4>
        <input type="text" placeholder="Add New Word" bind:value={theWord}>
        <button on:click={playGame} class="play-btn"> Let's Play </button>
    {:else}
        <div class="word-heading">
            <h2>Word of the Weekend</h2>
            <h3>{theWord}</h3>
        </div>
        
        <section>
            <PlayerCard playerName = "Begotten Son">
                <profile>
                    <img src="daniel-profile.jpg" alt="Begotten Son Profile">
                </profile>  
            </PlayerCard>
            <PlayerCard playerName = "AhkoteeKia">
                <profile>
                    <img src="kia-profile.jpg" alt="Kia Profile">
                </profile>  
            </PlayerCard>
        </section>
        <button on:click={newGame}>New Game</button>  
    {/if}    
</main>