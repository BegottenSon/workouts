<script>
	export let segment;
</script>

<style>
	nav {
		border-bottom: 1px solid rgba(0, 255, 34, 0.1);
		font-weight: 300;
		padding: 0 1em;
	}

	ul {
		display: flex;
		margin: 0;
		padding: 0;
	}

	/* clearfix */
	ul::after {
		content: '';
		display: block;
		clear: both;
	}

	li {
		display: block;
	}

	[aria-current] {
		position: relative;
		display: inline-block;
	}

	[aria-current]::after {
		position: absolute;
		content: '';
		width: calc(100% - 1em);
		height: 8px;
		background-image: url("data:image/svg+xml;charset=utf8,%3Csvg viewBox='0 0 800 215' xmlns='http://www.w3.org/2000/svg' fill-rule='evenodd' clip-rule='evenodd' stroke-linejoin='round' stroke-miterlimit='2'%3E%3Cpath d='M99.999874 2.354112l14.295615 61.15029 47.508394-41.069023-24.379346 57.87395 62.575882-5.301416-53.740511 32.492236 53.74051 32.492235-62.57588-5.301416 24.379345 57.87395-47.508394-41.069023-14.295615 61.15029-14.294647-61.15029-47.508394 41.069023 24.378377-57.87395-62.574912 5.301416 53.74051-32.492235L.000299 75.007913l62.574912 5.301416-24.378377-57.87395 47.508394 41.069024L99.999874 2.354112z' fill='%2318e500'/%3E%3Cpath d='M299.999874 2.354112l14.295615 61.15029 47.508394-41.069023-24.379346 57.87395 62.575882-5.301416-53.740511 32.492236 53.74051 32.492235-62.57588-5.301416 24.379345 57.87395-47.508394-41.069023-14.295615 61.15029-14.294647-61.15029-47.508394 41.069023 24.378377-57.87395-62.574912 5.301416 53.74051-32.492235-53.74051-32.492236 62.574912 5.301416-24.378377-57.87395 47.508394 41.069024 14.294647-61.150291z' fill='%2318e500'/%3E%3Cpath d='M499.999874 2.354112l14.295615 61.15029 47.508394-41.069023-24.379346 57.87395 62.575882-5.301416-53.740511 32.492236 53.74051 32.492235-62.57588-5.301416 24.379345 57.87395-47.508394-41.069023-14.295615 61.15029-14.294647-61.15029-47.508394 41.069023 24.378377-57.87395-62.574912 5.301416 53.74051-32.492235-53.74051-32.492236 62.574912 5.301416-24.378377-57.87395 47.508394 41.069024 14.294647-61.150291z' fill='%2318e500'/%3E%3Cpath d='M699.999874 2.354112l14.295615 61.15029 47.508394-41.069023-24.379346 57.87395 62.575882-5.301416-53.740511 32.492236 53.74051 32.492235-62.57588-5.301416 24.379345 57.87395-47.508394-41.069023-14.295615 61.15029-14.294647-61.15029-47.508394 41.069023 24.378377-57.87395-62.574912 5.301416 53.74051-32.492235-53.74051-32.492236 62.574912 5.301416-24.378377-57.87395 47.508394 41.069024 14.294647-61.150291z' fill='%2318e500'/%3E%3C/svg%3E");;
		display: block;
		bottom: -1px;
	}

	a {
		text-decoration: none;
		padding: 1em 0.5em;
		display: block;
	}
</style>

<nav>
	<ul>
		<li><a aria-current="{segment === undefined ? 'page' : undefined}" href=".">home</a></li>
		<li><a aria-current="{segment === 'bookworm' ? 'page' : undefined}" href="bookworm">bookworm game</a></li>
		<li><a aria-current="{segment === 'workouts' ? 'page' : undefined}" href="workouts">workouts</a></li>
		<li><a aria-current="{segment === 'brand' ? 'page' : undefined}" href="brand">brand guide</a></li>
		<!-- <li><a rel=prefetch aria-current="{segment === 'blog' ? 'page' : undefined}" href="blog">blog</a></li> -->
	</ul>
</nav>
