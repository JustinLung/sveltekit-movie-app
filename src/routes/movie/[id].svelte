<script context="module">
	const API_KEY = import.meta.env.VITE_API_KEY;
	const baseURL = 'https://api.themoviedb.org/3/search/api_key={api_key}Jack+Reacher';

	export async function load({ fetch, params }) {
		const res = await fetch(`${baseURL}/movie?api_key=${API_KEY}&query=${params.id}`);
		const data = await res.json();
		console.log(data);
		if (res.ok) {
			return {
				props: { searchedMovie: data.results }
			};
		}
	}
</script>

<script>
	export let searchedMovie
</script>

<section>
	<img src={`https://image.tmdb.org/t/p/w500${data.poster_path}`} alt={data.title} />
	<div>
		<h1>{data.title}</h1>
		<p>{data.overview}</p>
		<p>⭐️ <span>Rating:</span> {data.vote_average}</p>
		<a href="/" sveltekit:prefetch class="cta">Return Home</a>
	</div>
</section>

<style>
	section {
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 2em;
	}

	section h1 {
		font-size: 2em;
		padding: 0;
		margin: 0;
	}

	section p {
		font-size: 1.2rem;
		max-width: 30em;
	}

	section img {
		width: 25em;
		border-radius: 0.5em;
	}

	span {
		font-weight: bold;
	}

	.cta {
		padding: 0.7em 2em;
		color: #fff;
		background-color: #da4167;
		border: 2px solid #da4167;
		border-radius: 0.5em;
		text-decoration: none;
		transition: 0.3s ease-in-out;
	}

	.cta:hover {
		border: 2px solid #da4167;
		color: #da4167;
		background-color: transparent;
	}

	@media (max-width: 50em) {
		section {
			flex-direction: column;
		}
	}
</style>
