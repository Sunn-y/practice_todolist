<template>
<v-container app>
	<v-row>
		<v-col cols="9">
			<v-text-field label="✏ To do  " placeholder="take a walk" outlined v-model="newItem">
			</v-text-field>
		</v-col>
		<v-col cols="1">
			<v-btn dark color="#FFCCCC" height="60%" @click="addTodo">
				<v-icon>
					mdi-plus
				</v-icon>
			</v-btn>
		</v-col>
	</v-row>
	<v-alert v-if="check" text outlined color="#FF5050" icon="mdi-fire">
		Input something
	</v-alert>
</v-container>
</template>

<script>
export default {
	data: () => ({
		newItem: '',
		check: false
	}),
	methods: {
		addTodo() {
			if (this.newItem === '') {
				this.check = true;
				return;
			}
			if (this.newItem !== '') {
				this.check = false;
				var item = this.newItem.trim();
				this.$emit('addTodo', item);
				this.clearInput();
			}
		},
		clearInput() {
			this.newItem = '';
		}
	}
}
</script>

<style lang="css" scoped>
</style>
