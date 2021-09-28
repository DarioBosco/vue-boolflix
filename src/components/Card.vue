<template>
	<div>
		<div class="title">Titolo: {{ movie.title ? movie.title : movie.name }}</div>
		<div class="original_title">Titolo Originale: {{ movie.original_title ? movie.original_title : movie.original_name }}</div>
		<div class="lang">Language: <img :src="'https://www.countryflags.io/' + getFlag(movie.original_language) + '/shiny/64.png'" /></div>
		<div class="vote">
			Vote:
			<i v-for="n in Math.ceil(movie.vote_average / 2)" :key="n" class="fa fa-star full"></i>
			<i v-for="n in 5 - Math.ceil(movie.vote_average / 2)" :key="n" class="far fa-star empty"></i>
		</div>
		<hr />
	</div>
</template>

<script>
export default {
	props: {
		movie: Object,
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
	created() {},
};
</script>

<style>
@import '~@fortawesome/fontawesome-free/css/all.min.css';
.poster {
	height: 30px;
	width: 30px;
}

.full {
	color: red;
}

.empty {
	color: lightgray;
}
</style>
