<template>
	<section class="movies">
		<div>
			<div class="titolo">Titolo: {{ movie.title ? movie.title : movie.name }}</div>
		</div>
	</section>
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
</style>
