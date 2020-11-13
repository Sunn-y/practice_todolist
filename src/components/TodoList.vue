<template>
<v-list dense>
	<v-list-item-group color="#FF6666">
		<transition-group name="list" tag="ul">
			<v-list-item v-for="(item, i) in propsdata" :key="i">
				<v-list-item-content>
					<v-checkbox color="#FF6666"></v-checkbox>
				</v-list-item-content>
				<v-list-item-content>
					<v-list-item-title v-text="item"></v-list-item-title>
				</v-list-item-content>
				<v-spacer></v-spacer>
				<v-spacer></v-spacer>
				<v-spacer></v-spacer>
				<v-list-item-action>
					<v-list-item-icon @click="removeTodo(item, i)">
						<v-icon>mdi-trash-can</v-icon>
					</v-list-item-icon>
				</v-list-item-action>
			</v-list-item>
		</transition-group>
	</v-list-item-group>
</v-list>
</template>

<script>
export default {
	props: ['propsdata'],
	methods: {
		removeTodo(todoItem, index) {
			this.$emit('removeTodo', todoItem, index)
		}
	}
}
</script>

<style>
.list-move {
	transition: transform 2s;
}

.list-enter-active,
list-leave-active {
	transition: all 1s;
}

.list-enter,
list-leave-to {
	opacity: 0;
	transform: translateY(30px);
}
</style>
