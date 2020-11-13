<template>
<footer>
	<br>
	<br>
	<v-btn block large dark color="#FFCCCC" @click="clearTodo">
		Clear All
	</v-btn>
</footer>
</template>

<script>
export default {
	methods:{
		clearTodo(){
			this.$emit('removeAll');
		},
	}
}
</script>

<style lang="css" scoped>
</style>
