<template>
	<div>
		<h5>{{ title }} <span class="badge bg-secondary">{{ items.length }}</span></h5>
		<div class="card-body">
			<ul class="list-group">
				<li class="list-group-item d-flex justify-content-between align-items-center" v-for="item in items"
					v-bind:key="item">
					{{ item }}
					<button class="btn text-muted" v-on:click="deleteItem(item)">
						<i class="fa fa-trash"></i>
					</button>
				</li>
			</ul>
		</div>
		<div class="input-group my-1">
			<input type="text" v-model="item" v-on:keyup.enter="addItem(item)" class="form-control"
				placeholder="Prefixo">
			<div class="input-group-prepend">
				<button class="btn btn-outline-success mx-1" v-on:click="addItem(item)">
					<i class="fa fa-plus"></i>
				</button>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "ItemList",
	props: ["title", "items"],
	data() {
		return {
			item: ""
		}
	},
	methods: {
		addItem(item) {
			this.$emit("addItem", item)
			this.item = ""
		},
		deleteItem(item) {
			this.$emit("deleteItem", item)
		},

	}
}
</script>

<style scoped>
</style>
