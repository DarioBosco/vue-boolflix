<template>
	<section class="movies">
		<div v-if="APIQuery != ''" class="movie-card">
			<ul>
				<li v-for="(movie, index) in movies" :key="index">
					<div>Titolo: {{ movie.title }}</div>
					<div>Titolo Originale: {{ movie.original_title }}</div>
					<div>Lingua: {{ movie.original_language }}</div>
					<div>Voto: {{ movie.vote_count }}</div>
					<hr />
				</li>
			</ul>
		</div>
		<div v-else>Effettua una ricerca</div>
	</section>
</template>

<script>
export default {
	props: {
		movies: Array,
		APIQuery: String,
	},
};
</script>

<style></style>
