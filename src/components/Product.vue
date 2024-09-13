<script setup>
const props = defineProps({
	img: String,
	title: String,
	desc: String,
	price: Number,
});
</script>

<template>
	<div class="card">
		<img
			:src="img"
			:alt="img"
		/>
		<h1>{{ title }}</h1>
		<p>{{ desc }}</p>
		<h3>{{ price }}</h3>
	</div>
</template>

<style scoped>
.card {
  border: 1px solid black;
  padding: 1rem;
  width: 300px  ;
  min-height: 300px;
}

.card h1 {
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 1;
  line-clamp: 1;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap ;
}

.card img {
  width: 100%;
}
</style>
