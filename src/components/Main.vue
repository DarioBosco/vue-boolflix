<template>
	<main>
		<Card :movies="movies" :series="series" :APIQuery="APIQuery" />
	</main>
</template>

<script>
import Card from './Card.vue';
export default {
	props: {
		movies: Array,
		series: Array,
		APIQuery: String,
	},
	components: {
		Card,
	},
};
</script>

<style></style>
