<script setup lang="ts">
import { ref } from "vue"
import SearchResults from "./SearchResults.vue"

const SOME_KEY = process.env.SOME_KEY

const searchTerm = ref("")

const BASE_URL = "http://api.themoviedb.org/3/"

const API_URL = BASE_URL + "/discover/movie?sort_by=popularity.desc&" + SOME_KEY
</script>
<template>
	<div class="main-cont">
		<h1>Looking for movie stills?</h1>
		{{ searchTerm }}
		<el-form class="main-page-form">
			<el-form-item class="main-page-search-input">
				<el-input size="large" placeholder="right here" v-model="searchTerm" />
			</el-form-item>
		</el-form>
		<SearchResults />

		<el-pagination
			:page-size="5"
			:pager-count="11"
			layout="prev, pager, next"
			:total="100"
		>
			<!-- total = how many results found -->
		</el-pagination>
	</div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Rubik+Mono+One&display=swap");

/* .main-cont {
	display: flex;
	flex-direction: column;
} */
h1 {
	font-family: "Rubik Mono One", sans-serif;
	font-weight: normal;
	/* border: 1px rgba(255, 0, 0, 0.2) solid; */
	margin-bottom: 75px;
}

.main-page-form {
	display: flex;
	justify-content: center;
	/* border: 1px rgba(0, 0, 255, 0.2) solid; */
}
.main-page-search-input {
	width: 40em;
	color: tomato;
}
</style>
