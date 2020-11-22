<template>
	<div>
		<form v-on:submit.prevent="onSubmit">
			<input
				type="text"
				v-model="title"
				name="title"
				placeholder="Add Todo..."
			/>
			<input type="submit" value="Submit" class="btn" />
		</form>
	</div>
</template>

<script>
export default {
	name: "AddTodo",
	data() {
		return {
			title: "",
		};
	},
	methods: {
		onSubmit() {
			const newTodo = {
				title: this.title,
				completed: false,
			};
			this.$emit("add-todo", newTodo);

			this.title = "";
		},
	},
};
</script>

<style scoped>
form {
	display: flex;
}

input[type="text"] {
	flex: 10;
	padding: 5px;
}

input[type="submit"] {
	flex: 1;
}
</style>
