<template>
    <div class="container">
        <div class="row">
            <div class="col">
                <ItemList title="Prefixos" v-bind:items="prefixes" v-on:addItem="addPrefix"
                    v-on:deleteItem="deletePrefix"></ItemList>
            </div>

            <div class="col">
                <ItemList title="Sufixos" v-bind:items="sufixes" v-on:addItem="addSufix" v-on:deleteItem="deleteSufix">
                </ItemList>
            </div>
        </div>

        <h5>Dominios <span class="badge bg-secondary">{{ domains.length }}</span></h5>
        <div class="card">
            <div class="card-body">
                <ul class="list-group">
                    <li class="list-group-item" v-for="domain in domains" v-bind:key="domain.url">
                        <div class="row">
                            <div class="col-md text-start">
                                <span>
                                    {{ domain.url }}
                                </span>
                            </div>
                            <div class="col-md text-end">
                                <a class="btn bg-success" v-bind:href="domain.checkout" target="_blank">
                                    <i class="fa fa-shopping-cart text-white"></i>
                                </a>
                            </div>
                        </div>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css"
import "font-awesome/css/font-awesome.css"
import ItemList from "./ItemList.vue"

export default {
	name: "App",
	data: function () {
		return {
			prefix: "",
			sufix: "",
			prefixes: [],
			sufixes: []
		};
	},
	methods: {
		addPrefix(prefix) {
			this.prefixes.push(prefix);
			this.prefix = "";
		},
		addSufix(sufix) {
			this.sufixes.push(sufix);
			this.sufix = "";
		},
		deletePrefix(prefix) {
			this.prefixes.splice(this.prefixes.indexOf(prefix), 1);
		},
		deleteSufix(sufix) {
			this.sufixes.splice(this.sufixes.indexOf(sufix), 1);
		},
	},
	computed: {
		domains() {
			const domains = []
			for (let prefix of this.prefixes) {
				for (let sufix of this.sufixes) {
					const url = (prefix + sufix).toLowerCase()
					const checkout = `
						https://cart.hostgator.com.br/?pid=d&sld=${url}&tld=.com.br
					`
					domains.push({
						url,
						checkout
					})
				}
			}
			return domains
		}
	},
	components: {
		ItemList
	}
}
</script>

<style scoped>
</style>
