<script context="module">
	export async function load({ fetch, params }) {
		console.log('params', params.keyword);
		const res = await fetch(
			`https://api.themoviedb.org/3/search/multi?api_key=a43594e27080bd4a508140ffafb23dc6&language=en-US&query=${params.keyword}&page=1&include_adult=false`
		);
		const data = await res.json();
		console.log(data.results);

		if (res.ok) {
			return {
				props: {
					searchMoves: data.results
				}
			};
		}
	}
</script>

<script>
	import MovieCard from '../../components/MovieCard.svelte';
	import SearchMovie from '../../components/SearchMovie.svelte';
	import { fly } from 'svelte/transition';

	export let searchMoves;
</script>

<SearchMovie />
<section in:fly={{ y: 50, duration: 500 }} out:fly={{ duration: 500 }}>
	<div class="movie">
		{#each searchMoves as movie (movie.id)}
			<MovieCard {movie} />
		{:else}
			<p>No Movie Found for</p>
		{/each}
	</div>
</section>

<style>
	h2 {
		padding: 0 1rem;
		text-align: center;
	}
	.movie {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column-gap: 1rem;
		grid-row-gap: 1.5rem;
	}
	p {
		text-align: center;
		color: brown;
	}
</style>
