<script setup>
import Pagination from '@/components/Pagination.vue';
import Product from '@/components/Product.vue';
import Loading from '@/components/Loading.vue';
import axios from 'axios';
import { onMounted, ref, watch } from 'vue';

const products = ref([]);
const page = ref(1);
const perPage = ref(3);
const API_URL = `http://localhost:3000/products?_page=${page.value}&_per_page=${perPage.value}`;
const isLoading = ref(true);

onMounted(async () => {
	try {
		products.value = await axios.get(API_URL).then((res) => res.data);
	} catch (error) {
		console.log(error);
	} finally {
		isLoading.value = false;
	}
});

watch(page, async () => {
	try {
		isLoading.value = true;
		products.value = await axios.get(API_URL).then((res) => res.data);
	} catch (error) {
		console.log(error);
	} finally {
		isLoading.value = false;
	}
});

function changePage(newPage) {
	if (newPage < 1) return;
	if (newPage > products.value.pages) return;
	page.value = newPage;
}

console.log(page.value, API_URL);
</script>

<template>
	<main>
		<Loading v-if="isLoading" />
		<div
			class="products"
			v-else
		>
			<Product
				v-for="(product, index) in products.data"
				:key="index"
				:img="product.image"
				:title="product.title"
				:desc="product.desc"
				:price="product.price"
			/>
		</div>
		<div class="paginate">
			<Pagination
				:page="page"
				:totalPages="products.pages"
				@change-page="changePage"
			/>
		</div>
	</main>
</template>

<style scoped>
main {
	display: flex;
	gap: 2rem;
	flex-direction: column;
}

main .paginate {
	display: flex;
	gap: 2rem;
	align-items: center;
}

main .products {
	display: flex;
	flex-wrap: wrap;
	gap: 1.4rem;
}
</style>
