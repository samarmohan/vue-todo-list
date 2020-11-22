<template>
	<div id="container">
		<Header />
		<router-view />
	</div>
</template>

<script>
import Header from "./components/layout/Header";

export default {
	name: "App",
	components: {
		Header,
	},
};
</script>

<style>
#container {
	padding: 0 1rem;
}
</style>
