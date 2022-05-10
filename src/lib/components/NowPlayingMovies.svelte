<script>
	export let now_playing;
</script>

<h2>🚀 Now Playing</h2>
<div class="now-playing">
	{#each now_playing as movie}
		<a sveltekit:prefetch href={`/movie/${movie.id}`}>
			<img
				src={`https://image.tmdb.org/t/p/w500${movie.poster_path}`}
				alt={movie.title}
				class="movie-poster"
			/>
		</a>
	{/each}
</div>

<style>
	div {
		display: flex;
		justify-content: center;
		flex-wrap: wrap;
		gap: 1em;
	}

	img {
		width: 20em;
		border-radius: 0.5em;
		transition: 0.2s ease-in-out;
	}

	img:hover {
		transform: scale(0.9);
	}
</style>
