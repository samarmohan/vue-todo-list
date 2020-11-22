<template>
	<div
		class="todo-item"
		v-bind:class="{ 'is-complete': forEachTodo.completed }"
	>
		<p>
			<input type="checkbox" v-on:change="handleCompletedChange" />
			{{ forEachTodo.title }}
			<button v-on:click="$emit('del-todo', forEachTodo.id)" class="del">
				x
			</button>
		</p>
	</div>
</template>

<script>
export default {
	name: "TodoItem",
	props: ["forEachTodo"],
	methods: {
		handleCompletedChange() {
			this.forEachTodo.completed = !this.forEachTodo.completed;
		},
	},
};
</script>

<style>
.todo-item {
	background: #f4f4f4;
	padding: 10px;
	border-bottom: 1px #ccc dotted;
}

.is-complete {
	text-decoration: line-through;
}

.del {
	background: #ff0000;
	color: #fff;
	border: none;
	padding: 5px 10px;
	border-radius: 50%;
	cursor: pointer;
	float: right;
}
</style>
