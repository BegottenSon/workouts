<style>
    .load-wrapper {
        position: relative;
    }

    .inner-circle {
        height: 4em;
        width: 4em;
        background-color: var(--gum);
        border-radius: 50em;
        animation: pulse 3s linear infinite;
    }

    @keyframes pulse {
        0%, 50%, 100% {
            transform: scale(1);
            filter: blur(0);
        }
        25% {
            transform: scale(0.6);
            filter: blur(5px);
        }
        75% {
            transform: scale(1.4);
            filter: blur(5px);
        }
    }

    /* .outer-circle {
        position: relative;
        top: 50%;
        left: 50%;
        height: 6em;
        width: 6em;
        background-color: var(--purple);
    } */
</style>

<div class="load-wrapper">
    <div class="outer-circle">
        <div class="inner-circle"></div>
    </div>
</div>