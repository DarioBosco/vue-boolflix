<template>
	<div id="app">
		<Header @searchHasChanged="searchHasChanged" />
		<Main :movies="movies" :APIQuery="APIQuery" />
	</div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
	name: 'App',
	data() {
		return {
			API_KEY: '87dd413a911650468c247310a01a7d52',
			movies: [],
			APIQuery: '',
		};
	},
	components: {
		Header,
		Main,
	},
	props: {
		searchText: String,
	},
	methods: {
		searchHasChanged(res) {
			this.APIQuery = res;
			this.fetchMovies();
			this.fetchSeries();
		},
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
		fetchSeries() {
			axios
				.get('https://api.themoviedb.org/3/search/tv/?api_key=' + this.API_KEY + '&query=' + this.APIQuery)
				.then((res) => {
					this.movies = [...this.movies, ...res.data.results];
				})
				.catch((error) => {
					console.log(error);
				});
		},
	},
	created() {
		this.fetchMovies();
		this.fetchSeries();
	},
};
</script>

<style lang="scss"></style>
