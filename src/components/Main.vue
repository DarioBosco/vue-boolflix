<template>
	<main>
		<MovieCard :movies="movies" :series="series" :APIQuery="APIQuery" />
	</main>
</template>

<script>
import MovieCard from './MovieCard.vue';
export default {
	props: {
		movies: Array,
		series: Array,
		APIQuery: String,
	},
	components: {
		MovieCard,
	},
};
</script>

<style></style>
