<template>
	<div>
		<div v-bind:key="forEachTodo.id" v-for="forEachTodo in todos">
			<TodoItem
				v-on:del-todo="$emit('del-todo', forEachTodo.id)"
				v-bind:forEachTodo="forEachTodo"
			/>
		</div>
	</div>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
	components: {
		TodoItem,
	},
	name: "Todos",
	props: ["todos"],
};
</script>

<style scoped></style>
