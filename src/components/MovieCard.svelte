<script>
	export let movie;
	console.log(movie);
</script>

<div>
	<a sveltekit:prefetch href={'/movie/' + movie.id}>
		<div class="movie-card">
			<img src={'https://image.tmdb.org/t/p/w300' + movie.poster_path} alt="" />
		</div>
		<div class="movie-descriptopn">
			<h2>{movie.title}</h2>
			<p>{movie.release_date}</p>
		</div></a
	>
</div>

<style>
    a{
        text-decoration: none;
        color: inherit;
    }
	.movie-card img {
		width: 100%;
		height: 30vh;
		object-fit: cover;
		border-radius: 1rem;
	}
	h2 {
		font-size: 0.9rem;
		margin-bottom: 0;
	}
	p {
		font-size: 0.7rem;
		margin: 4px 0 0;
	}
</style>
