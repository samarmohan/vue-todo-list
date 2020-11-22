<template>
	<div id="app">
		<AddTodo v-on:add-todo="addTodo" />
		<Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
	</div>
</template>

<script>
import axios from "axios";

import Todos from "../components/todo/Todos";
import AddTodo from "../components/form/AddTodo";

export default {
	name: "Home",
	components: {
		Todos,
		AddTodo,
	},
	data() {
		return {
			todos: [],
		};
	},
	methods: {
		deleteTodo(id) {
			axios
				.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
				.then(
					(res) =>
						(this.todos = this.todos.filter(
							(todo) => todo.id !== id,
							res.data
						))
				)
				.catch((err) => console.log(err));
		},
		addTodo(newTodo) {
			const { title, completed } = newTodo;

			axios
				.post("https://jsonplaceholder.typicode.com/todos", {
					title,
					completed,
				})
				.then((res) => (this.todos = [...this.todos, res.data]))
				.catch((err) => console.log(err));
		},
	},
	created() {
		axios
			.get(
				"https://jsonplaceholder.typicode.com/todos?_limit=10&completed=false"
			)
			.then((res) => (this.todos = res.data));
	},
};
</script>

<style>
* {
	box-sizing: border-box;
	margin: 0%;
	padding: 0%;
}

body {
	font-family: Arial, Helvetica, sans-serif;
	line-height: 1.4;
}

.btn {
	display: inline-block;
	border: none;
	background: #555;
	color: #fff;
	padding: 7px 20px;
	cursor: pointer;
}

.btn:hover {
	background: #666;
}
</style>
