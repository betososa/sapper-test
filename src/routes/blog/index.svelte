<script context="module">
	export function preload({ params, query }) {
		return this.fetch(`https://jsonplaceholder.typicode.com/todos/1`).then(r => r.json()).then(todo => {
			return { todo };
		});
	}
</script>

<script>
	export let todo;
</script>

<style>
	ul {
		margin: 0 0 1em 0;
		line-height: 1.5;
	}
</style>

<svelte:head>
	<title>{todo.title}</title>
	<meta property="og:title" content={todo.title} />
	<meta property="og:type" content="video.movie" />
	<meta property="og:url" content={todo.title} />
	<meta property="og:image" content="http://ia.media-imdb.com/images/rock.jpg" />
</svelte:head>

<h1>Recent posts</h1>

<ul>
	{#each posts as post}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
		<li><a rel='prefetch' href='blog/{post.slug}'>{post.title}</a></li>
	{/each}
</ul>
