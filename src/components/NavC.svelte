<script>
    // export let segment = 'home';
    let selected = 'home';
</script>

<nav>
	<ul>
		<li><a class:selected="{selected === 'home'}" class="nav-links" on:click="{() => {selected = 'home'}}" href="workouts">home</a></li>
        <li><a class:selected="{selected === 'workouts'}" class="nav-links" on:click="{() => {selected = 'workouts'}}" href="workouts">workouts</a></li>
        <li><a class:selected="{selected === 'away'}" class="nav-links" on:click="{() => {selected = 'away'}}" href="workouts">away</a></li>
	</ul>
</nav>

<style>
    nav{
        position: relative;
    }

    ul {
        display: flex;
        align-content: space-between;
        list-style: none;
    }

    li {
        padding: 0 1em;
    }

    a {
        text-decoration: none;
    }

    .nav-links {
        padding: 0.6em;
    }

    .selected {
        background-color: rgb(6, 160, 160);
        padding: 0.6em;
        border-radius: 8px;
        left: 4em;
        transition: 0.2s ease; 
    }

</style>