<script>
    const ringPath = "M200.000528 65.505506c74.228607 0 134.494047 60.26544 134.494047 134.495721 0 74.228608-60.26544 134.494048-134.494047 134.494048-74.230282 0-134.494048-60.26544-134.494048-134.494048 0-74.230281 60.263766-134.495721 134.494048-134.495721zm0 1.55853c73.369825 0 132.935516 59.567366 132.935516 132.937191 0 73.369825-59.565691 132.935517-132.935516 132.935517s-132.93719-59.565692-132.93719-132.935517 59.567365-132.93719 132.93719-132.93719z"
</script>

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

   

    svg {
        width:  10em;
        height:  10em;
    }

   .center-circle {
       transform-origin: center;
       animation: pulse 3s linear infinite;
   }

   .inner-ring {
       animation: ring-color 1s ease-out infinite alternate;
   }

   .diamond-tri{
       transform-origin: center;
       animation: rotating-orbs 3s linear infinite;
   }

   .orb-1 {
       transform: translate(38px, 180px);
        /* transform-origin:  top left ; */
        animation: shrink 1s linear infinite;
   }

   .outer-ring {
       transform-origin: center;
       animation: out-ring 1.5s linear infinite alternate;
   }
   /* ANIMATION SETTINGS */
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
            transform: scale(1.1);
            filter: blur(5px);
        }
    }

    @keyframes ring-color {
        0% {
            fill: #b101d0;
        }
        50% {
            fill: var(--gum);
        }
        100% {
            fill: #fff321;
        }
    }

    @keyframes shrink {
        50%, 100% {
            transform: translate(65px, 200px) scale(0);
        }
    }

    @keyframes rotating-orbs {
        to {
            transform: rotate(360deg);
        }
    }

    @keyframes out-ring {
        to {
            transform: skew(70deg) scale(0.1);
        }
    }
</style>

<!-- <div class="load-wrapper">
    <div class="outer-circle">
        <div class="inner-circle"></div>
    </div>
</div> -->

<svg viewBox="0 0 400 400" xmlns="http://www.w3.org/2000/svg" fill-rule="evenodd" clip-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="2">
    <path class="inner-ring" d="M200.000528 65.505506c74.228607 0 134.494047 60.26544 134.494047 134.495721 0 74.228608-60.26544 134.494048-134.494047 134.494048-74.230282 0-134.494048-60.26544-134.494048-134.494048 0-74.230281 60.263766-134.495721 134.494048-134.495721zm0 1.55853c73.369825 0 132.935516 59.567366 132.935516 132.937191 0 73.369825-59.565691 132.935517-132.935516 132.935517s-132.93719-59.565692-132.93719-132.935517 59.567365-132.93719 132.93719-132.93719z" fill="#b101d0"/>
    <circle class="orb-1" cx="28.215" cy="24.311" r="7.36" fill="#fff321" />
    <circle class="orb-2" cx="28.215" cy="24.311" r="7.36" fill="#fff321" transform="matrix(1.14258 0 0 1.14258 300.697829 172.222377)"/>
    <path class="diamond-tri" d="M200.03421 324.525499l8.374888 16.749777h-16.749777l8.374889-16.749777zM199.9995 58.654124l8.408483 8.408483-8.408483 8.40976-8.40976-8.40976 8.40976-8.408483z" fill="#fff321"/>
    <!-- <path class="outer-ring" d="M200 0c110.383 0 200 89.617 200 200s-89.617 200-200 200S0 310.383 0 200 89.617 0 200 0zm0 50c82.787 0 150 67.213 150 150s-67.213 150-150 150S50 282.787 50 200 117.213 50 200 50z" fill="#b101d0"/> -->
    <g transform="translate(85.5177 85.5177) scale(.57241)">
        <circle class="center-circle" cx="200" cy="200" r="200" fill="#b101d0"/>
    </g>
</svg>