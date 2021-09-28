<template>
	<main>
		<div v-if="APIQuery != ''">
			<Card v-for="movie in movies" :key="movie.id" :movie="movie" />
		</div>
		<div v-else>
			Effettua una ricerca
		</div>
	</main>
</template>

<script>
import Card from './Card.vue';
export default {
	props: {
		movies: Array,
		APIQuery: String,
	},
	components: {
		Card,
	},
};
</script>

<style></style>
