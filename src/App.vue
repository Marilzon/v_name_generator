<template>
	<div>
		<header class="header text-center">
			<h1>V NAME GENERATOR <span class="fa fa-check text-success"></span></h1>
			<h5>Gerador de nomes para seu projeto</h5>
			<div class="tags-stacks">
				<span class="badge text-bg-success m-1">Vue.js</span>
				<span class="badge text-bg-success m-1">GraphQL</span>
				<span class="badge text-bg-success m-1">NodeJS</span>
			</div>
		</header>

		<div id="main">
			<div class="container">
				<div class="row">

					<div class="col">
						<h5>Prefixos <span class="badge bg-secondary">{{ prefixes.length }}</span></h5>
						<div class="card-body">
							<ul class="list-group">
								<li class="list-group-item d-flex justify-content-between align-items-center" v-for="prefix in prefixes" v-bind:key="prefix">
									{{ prefix }}
									<button class="btn text-muted" v-on:click="deletePrefix(prefix)"><i class="fa fa-trash"></i></button>
								</li>
							</ul>
						</div>
						<div class="input-group my-1">
							<input type="text" v-model="prefix" v-on:keyup.enter="addPrefix(prefix)" class="form-control" placeholder="Prefixo">
							<div class="input-group-prepend">
								<button class="btn btn-outline-success mx-1" v-on:click="addPrefix(prefix)">
									<i class="fa fa-plus"></i>
								</button>
							</div>
						</div>
					</div>

					<div class="col">
						<h5>Sufixos <span class="badge bg-secondary">{{ sufixes.length }}</span></h5>
						<div class="card-body">
							<ul class="list-group">
								<li class="list-group-item d-flex justify-content-between align-items-center" v-for="sufix in sufixes" v-bind:key="sufix">
									{{ sufix }}
									<button class="btn text-muted" v-on:click="deleteSufix(sufix)"><i class="fa fa-trash"></i></button>
								</li>
							</ul>
						</div>
						<div class="input-group my-1">
							<input type="text" v-model="sufix" v-on:keyup.enter="addSufix(sufix)"  class="form-control" placeholder="Sufixo">
							<div class="input-group-prepend">
								<button class="btn btn-outline-success mx-1" v-on:click="addSufix(sufix)">
									<i class="fa fa-plus"></i>
								</button>
							</div>
						</div>
					</div>
				</div>

				<h5>Dominios <span class="badge bg-secondary">{{ domains.length }}</span></h5>
				<div class="card">
					<div class="card-body">
						<ul class="list-group">
							<li class="list-group-item" v-for="domain in domains" v-bind:key="domain">
								{{ domain }}
							</li>
						</ul>
					</div>
				</div>

			</div>
		</div>
	</div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css"
import "font-awesome/css/font-awesome.css"

export default {
	name: "App",
	data: function () {
		return {
			prefix: "",
			sufix: "",
			prefixes: [],
			sufixes: [],
			domains: []
		}
	},
	methods: {
		addPrefix(prefix) {
			this.prefixes.push(prefix)
			this.prefix = ""
		},
		addSufix(sufix) {
			this.sufixes.push(sufix)
			this.sufix = ""
			this.generateDomain()
		},
		deletePrefix(prefix) {
			this.prefixes.splice(this.prefixes.indexOf(prefix), 1)
			this.generateDomain()
		},
		deleteSufix(sufix) {
			this.sufixes.splice(this.sufixes.indexOf(sufix), 1)
			this.generateDomain()
		},
		generateDomain() {
			this.domains = []
			for (let prefix of this.prefixes) {
				for (let sufix of this.sufixes) {
					this.domains.push(prefix + sufix)
				}
			}
		}
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

.form-control:focus {
	color: #212529;
	background-color: #fff;
	border-color: #86fe92;
	outline: 0;
	box-shadow: 0 0 0 0.1rem rgba(57, 253, 13, 0.25);
}
</style>
