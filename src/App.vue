<template>
	<the-header></the-header>
    <h1>Hello World.</h1>
    <base-button></base-button>
	<the-footer></the-footer>
</template>

<script>
import TheHeader from "./components/TheHeader.vue"
import TheFooter from "./components/TheFooter.vue"
export default {
    name: "App",
    components: {
		TheHeader,
		TheFooter
	}
};
</script>

<style>
* {
	margin: 0;
	padding: 0;
}
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}
</style>
