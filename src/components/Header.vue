<template>
	<header>
		<input v-model="inputText" type="text" />
		<button @click="$emit('searchHasChanged', inputText)" >Cerca</button>
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

<style></style>
