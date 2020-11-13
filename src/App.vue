<template>
<div id="app">
	<TodoHeader></TodoHeader>
	<TodoInput v-on:addTodo="saveTodo"></TodoInput>
	<TodoList v-bind:propsdata="todoItems" v-on:removeTodo="removeOne"></TodoList>
	<TodoFooter v-on:removeAll="clearAll"></TodoFooter>
</div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'
export default {
	name: 'app',
	components: {
		TodoHeader,
		TodoInput,
		TodoList,
		TodoFooter
	},
	data() {
		return {
			todoItems: []
		}
	},
	created() {
		if (localStorage.length > 0) {
			for (var i = 0; i < localStorage.length; i++) {
				this.todoItems.push(localStorage.key(i));
			}
		}
	},
	methods: {
		saveTodo(todoItem) {
			localStorage.setItem(todoItem, todoItem);
			this.todoItems.push(todoItem);
		},
		clearAll() {
			localStorage.clear();
			this.todoItems = [];
		},
		removeOne(todoItem, index) {
			localStorage.removeItem(todoItem);
			this.todoItems.splice(index, 1);
		}
	}
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Hi+Melody&display=swap');

* {
	font-family: 'Hi Melody', cursive;
	font-size: 1.2em;
}
</style>
