<template>
	<div>
		<header class="header text-center">
			<h1>V NAME GENERATOR <span class="fa fa-check text-success"></span></h1>
			<h5>Gerador de nomes para seu dominio</h5>
			<div class="tags-stacks">
				<span class="badge text-bg-success m-1">Vue.js</span>
				<span class="badge text-bg-success m-1">GraphQL</span>
				<span class="badge text-bg-success m-1">NodeJS</span>
			</div>
		</header>

		<div id="main">
			<DomainList></DomainList>
		</div>
	</div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css"
import "font-awesome/css/font-awesome.css"
import DomainList from "./components/DomainList.vue";

export default {
	name: "App",
	components: {
		DomainList,
	}
}
</script>

<style>
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
	font-weight: 400;
	-webkit-font-smooth: antialiased;
	list-style: none;
}

.header {
	background-color: rgba(169, 255, 160, 0.297);
	padding: 1rem 0;
	margin-bottom: 1rem;
}

.main {
	background-color: #f1f1f1;
}
</style>
