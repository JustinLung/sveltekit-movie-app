<script context="module">
	const API_KEY = import.meta.env.VITE_API_KEY;
	const baseURL = 'https://api.themoviedb.org/3/movie';
	const nowPlayingEndpoint = `/now_playing?api_key=${API_KEY}&language=en-US&page=1`;

	export async function load({ fetch }) {
		const res = await fetch(`${baseURL}${nowPlayingEndpoint}`);
		const data = await res.json();
		if (res.ok) {
			return {
				props: { now_playing: data.results }
			};
		}
	}
</script>

<script>
	import NowPlayingMovies from '../lib/components/NowPlayingMovies.svelte';
	import SearchMovies from '../lib/components/SearchMovie.svelte';
	export let now_playing;
</script>

<section>
	<SearchMovies />
	<NowPlayingMovies {now_playing} />
</section>
