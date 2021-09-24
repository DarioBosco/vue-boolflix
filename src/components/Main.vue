<template>
	<main>
		<MovieCard :movies="movies" :APIQuery="APIQuery" />
	</main>
</template>

<script>
import MovieCard from './MovieCard.vue';
export default {
	props: {
		movies: Array,
		APIQuery: String,
	},
	components: {
		MovieCard,
	},
};
</script>

<style></style>
