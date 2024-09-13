<script setup>
const props = defineProps({
	page: Number,
	totalPages: Number,
});

const emits = defineEmits(['change-page']);

function changePage(newPage) {
	emits('change-page', newPage);
}
</script>

<template>
	<button
		@click="changePage(page - 1)"
		v-show="page > 1"
	>
		prev
	</button>
	<p>Page {{ page }} of {{ totalPages }}</p>
	<button
		@click="changePage(page + 1)"
		v-show="page < totalPages"
	>
		next
	</button>
</template>
