<script>
	let src = "dj-in-hammock.jpg";

</script>

<style>

:global(body) {
	background-color: var(--dark-green);
}

	h1, figure, p {
		text-align: center;
		margin: 0 auto;
	}

	h1 {
		font-size: 2.8em;
		text-transform: uppercase;
		font-weight: 700;
		margin: 0 0 0.5em 0;
	}

	figure {
		margin: 0 0 1em 0;
	}

	img {
		width: 100%;
		max-width: 400px;
		max-height: 400px;
		margin: 0 0 1em 0;
		border-radius: 8px;
		object-fit: cover;
		object-position: 0% 90%;
		filter: saturate(0.5);
	}

	p {
		margin: 1em auto;
	}

</style>

<svelte:head>
	<title>Workouts in Sapper</title>
</svelte:head>

<h1>Let's Workout On'em</h1>

<figure>
	<a href="workouts"><img alt='Success Kid' {src}></a>
	<figcaption>Gotta Love'em</figcaption>
</figure>

<p><strong>Figured it out in vanilla? Let's work it in Sapper</strong></p>
