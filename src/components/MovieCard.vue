<template>
	<section class="movies">
		<div v-if="APIQuery != ''" class="movie-card">
			<ul>
				<li v-for="(movie, index) in movies" :key="index">
					<div>Titolo: {{ movie.title }}</div>
					<div>Titolo Originale: {{ movie.original_title }}</div>
					<div>Lingua: <img :src="'https://www.countryflags.io/' + getFlag(movie.original_language) + '/shiny/32.png'" /></div>
					<div>Voto: {{ movie.vote_average }}</div>
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
	methods: {
		getFlag(country) {
			if (country === 'en') {
				return 'GB';
			} else if (country === 'ja') {
				return 'JP';
			} else if (country === 'el') {
				return 'GR';
			}
			return country.toUpperCase();
		},
	},
};
</script>

<style></style>
