<script setup>
import { RouterView } from 'vue-router';
import HomeView from './views/HomeView.vue';
</script>

<template>
	<RouterView />
	 <!-- <Suspense>
		<template #default>
			<HomeView/>
		</template>
		<template #fallback>
			<div class="loading"></div>
		</template>
	 </Suspense> -->
</template>

<style scoped>
.loading {
	height: 200px;
	width: 200px;
	background-color: red;
}
</style>
