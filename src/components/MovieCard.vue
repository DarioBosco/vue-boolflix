<template>
	<section class="movies">
		<div v-if="APIQuery != ''" class="movie-card">
			<ul class="movies">
				<li v-for="(movie, index) in movies" :key="index">
					<div>Titolo: {{ movie.title }}</div>
					<div>Titolo Originale: {{ movie.original_title }}</div>
					<div>Lingua: <img :src="'https://www.countryflags.io/' + getFlag(movie.original_language) + '/shiny/32.png'" /></div>
					<div>Voto: {{ movie.vote_average }}</div>
					<hr />
				</li>
			</ul>
			<ul class="series">
				<li v-for="(serie, index) in series" :key="index">
					<div>Titolo: {{ serie.name }}</div>
					<div>Titolo Originale: {{ serie.original_name }}</div>
					<div>Lingua: <img :src="'https://www.countryflags.io/' + getFlag(serie.original_language) + '/shiny/32.png'" /></div>
					<div>Voto: {{ serie.vote_average }}</div>
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
		series: Array,
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
