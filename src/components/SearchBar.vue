<template>
	<div id="search-bar" class="col-sm-12">
		<div class="form-group">
			<div class="input-group">
				<input type="text" class="form-control" v-on:keyup.enter="onSearch" v-model="query">
				<div class="input-group-btn">
					<button class="btn btn-danger" v-on:click="onSearch">search</button>
				</div>
			</div>
		</div>
	</div>
</template>


<script>

import Vue from 'vue'

export default {
	name: 'search-bar',
	data: function() {
		return {
			query: ''
		}
	},
	methods: {
		onSearch() {
			const URL = `https://api-v2.hearthis.at/search/tracks/?t=${this.query}`;
			 Vue.axios.get(URL)
			.then((response) => {
				 this.$emit('dataMusic', response.data)
			});
			

		}
	}
}
	
</script>