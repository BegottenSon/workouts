<script>
    let checked = false;
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
        transform: translateX(-5em);
        border-radius: 2em;
        border: 2px solid var(--gum);
        background-color: var(--gum);
        transition: 300ms 280ms cubic-bezier(0,.42,.5,1.04);
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
        top: -2.9em;
        width: 0.12em;
        height: 4em;
        background-color: rgb(229, 198, 240);
    }

    #rightString {
        position: absolute;
        top: -2.9em;
        width: 0.12em;
        height: 4em;
        background-color: rgb(229, 198, 240);
        
    }

    #centerString {
        position: absolute;
        top: -2.9em;
        left: 1.2em;
        width: 0.12em;
        height: 4em;
        background-color: rgb(229, 198, 240);
    }

    .left-string-original {
        transform: translateX(-3em) rotate(20deg);
        transition: 300ms 280ms cubic-bezier(0,.42,.5,1.04);
    }
    .left-string-move {
        transform: translateX(-1.3em);
        transition: 300ms cubic-bezier(0.95, -0.02, 0.71, 1);
    }

    .right-string-original {
        transform: translateX(3.8em);
        transition: 300ms cubic-bezier(0.95, -0.02, 0.71, 1);
    }
    .right-string-move {
        transform: translateX(4.8em) rotate(-20deg);
        transition: 300ms 280ms cubic-bezier(0,.42,.5,1.04);
    }

    #toggleFriction:checked + #balls:before {
        transform: translateX(-2.7em);
        transition: 300ms cubic-bezier(0.95, -0.02, 0.71, 1);
    }

    #toggleFriction:checked + #balls:after {
        transform: translateX(4.5em);
        transition: 300ms 280ms cubic-bezier(0,.42,.5,1.04);
    }

    

</style>

<section>
    <h1> Kinetic Toggle </h1>
    <div class="toggle">
        <div id="leftString" class="{checked ? 'left-string-move' : 'left-string-original'}"></div>
        <div id="rightString" class="{checked ? 'right-string-move' : 'right-string-original'}"></div>
        <div id="centerString"></div>
         <input type="checkbox" bind:checked id="toggleFriction"> 
         <label for="toggleFriction" id="balls"></label> 
          
    </div>
</section>