<script context="module">
	export async function load({ fetch }) {
		const apiKey = 'a43594e27080bd4a508140ffafb23dc6';

		const res = await fetch(
			'https://api.themoviedb.org/3/movie/popular?api_key=a43594e27080bd4a508140ffafb23dc6&language=en-US&page=1'
		);

		const data = await res.json();
		if (res.ok) {
			return {
				props: {
					populer: data.results
				}
			};
		}
	}
</script>

<script>
	import Populer from '../components/Populer.svelte';
	import SearchMovie from '../components/SearchMovie.svelte';
	import '../style/global.css';
	import {fly} from "svelte/transition"

	export let populer;
</script>


	<div  in:fly={{duration:500}} out:fly={{duration:500}}>
		<SearchMovie />
	</div>
	<div in:fly={{y:50, duration:500, delay:500}} out:fly={{duration:500}}>
		<Populer  movies={populer} />
	</div>
	

