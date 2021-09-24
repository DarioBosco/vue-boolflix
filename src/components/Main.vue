<template>
	<main>
		<ul>
			<li v-for="(movie, index) in movies" :key="index">
				<div>Titolo: {{ movie.title }}</div>
				<div>Titolo Originale: {{ movie.original_title }}</div>
				<div>Lingua: {{ movie.original_language }}</div>
				<div>Voto: {{ movie.vote_count }}</div>
				<hr />
			</li>
		</ul>
	</main>
</template>

<script>
import axios from 'axios';
export default {
	data() {
		return {
			API_KEY: '87dd413a911650468c247310a01a7d52',
			APIQuery: 'rick',
			movies: [],
		};
	},
	methods: {
		fetchMovies() {
			axios
				.get('https://api.themoviedb.org/3/search/movie/?api_key=' + this.API_KEY + '&query=' + this.APIQuery)
				.then((res) => {
					this.movies = res.data.results;
				})
				.catch((error) => {
					console.log(error);
				});
		},
	},
	created() {
		this.fetchMovies();
	},
};
</script>

<style></style>
