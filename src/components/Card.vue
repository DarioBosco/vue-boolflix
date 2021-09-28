<template>
	<div class="flip-card">
		<div class="flip-card-inner">
			<div class="flip-card-front">
				<img :src="'https://image.tmdb.org/t/p/w342/' + movie.poster_path" alt="" />
			</div>
			<div class="flip-card-back">
				<div class="back">
					<div class="title"><span>Title: </span>{{ movie.title ? movie.title : movie.name }}</div>
					<div class="original_title"><span>Original Title: </span>{{ movie.original_title ? movie.original_title : movie.original_name }}</div>
					<div class="lang"><span>Language: </span><img :src="'https://www.countryflags.io/' + getFlag(movie.original_language) + '/shiny/32.png'" /></div>
					<div class="vote">
						<span>Vote: </span>
						<i v-for="n in Math.ceil(movie.vote_average / 2)" :key="n" class="fa fa-star full"></i>
						<i v-for="n in 5 - Math.ceil(movie.vote_average / 2)" :key="n" class="far fa-star empty"></i>
					</div>
					<div class="overview"><span>Overview: </span> {{ movie.overview }}</div>
				</div>
			</div>
		</div>
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

/* The flip card container - set the width and height to whatever you want. We have added the border property to demonstrate that the flip itself goes out of the box on hover (remove perspective if you don't want the 3D effect */
.flip-card {
	background-color: transparent;
	width: 342px;
	height: 500px;
	/* perspective: 1000px; */ /* Remove this if you don't want the 3D effect */
	margin: 25px 0px 25px 0px;
	overflow: hidden;
}

/* This container is needed to position the front and back side */
.flip-card-inner {
	position: relative;
	width: 100%;
	height: 100%;
	text-align: center;
	transition: transform 0.8s;
	transform-style: preserve-3d;
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.flip-card:hover .flip-card-inner {
	transform: rotateY(180deg);
}

/* Position the front and back side */
.flip-card-front,
.flip-card-back {
	position: absolute;
	width: 100%;
	height: 100%;
	-webkit-backface-visibility: hidden; /* Safari */
	backface-visibility: hidden;
}

/* Style the front side (fallback if image is missing) */
.flip-card-front {
	background-image: url(../assets/placeholder.png);
	background-position: center;
}

.flip-card-front img {
	height: 100%;
	object-fit: cover;
	width: 100%;
}

/* Style the back side */
.flip-card-back {
	text-align: left;
	padding: 20px;
	background-color: black;
	color: white;
	transform: rotateY(180deg);
}

.flip-card-back div {
	margin-bottom: 10px;
}

.lang {
	display: flex;
	align-items: center;
}

span {
	font-weight: bold;
}
</style>
