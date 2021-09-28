<template>
	<header>
		<div class="logo">BOOLFLIX</div>
		<div class="search">
			<input v-model="inputText" type="text" @keyup.enter="$emit('searchHasChanged', inputText)" />
			<button @click="$emit('searchHasChanged', inputText)">Cerca</button>
		</div>
	</header>
</template>

<script>
export default {
	data() {
		return {
			inputText: '',
		};
	},
};
</script>

<style>
header {
	height: 100px;
	background: black;
	display: flex;
	justify-content: space-between;
	align-items: center;
}

.logo {
	padding-left: 20px;
	color: red;
	font-size: 3rem;
}

.search {
	padding-right: 20px;
}
</style>
