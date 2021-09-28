<template>
	<main>
		<div v-if="APIQuery != ''" class="container">
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

<style>
main {
	background-color: grey;
	height: calc(100vh - 100px);
	width: 100%;
	overflow-y: auto;
	scrollbar-width: thin;
	scrollbar-color: red grey;
}
.container {
	display: flex;
	flex-wrap: wrap;
	justify-content: space-evenly;
}
</style>
