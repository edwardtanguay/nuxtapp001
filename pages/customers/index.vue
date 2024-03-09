<script setup>
// const { pending, data: products } = await useFetch( // also works

// const { pending, data: products } = useFetch(
// 	"https://fakestoreapi.com/products/1",
// 	{
// 		lazy: false,
// 		pick: ["id", "image", "title"],
// 	}
// );

const {
	pending,
	data: products,
	refresh,
} = useFetch("https://fakestoreapi.com/products", {
	lazy: true,
	transform: (products) => {
		return products.map((product) => ({
			id: product.id,
			title: product.title,
			image: product.image,
		}));
	},
});
</script>

<template>
	<div v-if="pending">
		<p>Loading...</p>
	</div>
	<div v-else>
		<button @click="refresh">refresh data</button>
		<h2 class="text-xl mb-3 mt-6">{{ products.length }} products</h2>
		<ul>
			<li
				v-for="product in products"
				class="flex gap-3 items-center mb-3 text-xl"
			>
				<img
					class="w-[3rem] rounded border-4 border-white"
					:src="product.image"
				/>
				<div>
					{{ product.title }}
				</div>
			</li>
		</ul>
	</div>
</template>
