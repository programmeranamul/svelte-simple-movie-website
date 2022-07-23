<script context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/${params.id}?api_key=a43594e27080bd4a508140ffafb23dc6&language=en-US`
		);
		const data = await res.json();

		if (res.ok) {
			return {
				props: {
					details: data
				}
			};
		}
	}
</script>

<script>
	export let details;
	import global from '../../style/global.css';
	import { fly } from 'svelte/transition';
</script>

<div
	class="movie-details"
	in:fly={{ y: 50, duration: 500, delay: 500 }}
	out:fly={{ duration: 500 }}
>
	<div class="img-container">
		<img src={'https://image.tmdb.org/t/p/original' + details.backdrop_path} alt={details.title} />
	</div>
	<div class="text-container">
		<h2>{details.title}</h2>
		<p class="over-view">
			{details.overview}
		</p>
		<p>
			<span>Release date :</span>
			{details.release_date} <br />
			<span>Budget :</span>
			{details.budget} <br />
			<span>Rating :</span>
			{details.vote_average} <br />
			<span>Runtime :</span>
			{details.runtime}mins
		</p>
	</div>
</div>

<style>
	.movie-details {
		margin: 2% 0 10%;
	}
	.img-container {
		width: 100%;
	}
	.img-container img {
		width: 100%;
		border-radius: 1rem;
		margin-bottom: 1rem;
		object-fit: cover;
	}
	h2 {
		font-size: 1.5rem;
	}
	p span {
		font-weight: bold;
	}
</style>
