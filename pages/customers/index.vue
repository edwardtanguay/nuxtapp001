<script setup>
const url = "https://edwardtanguay.vercel.app/share/employees.json";
const { data: employees } = useFetch(() => url);
// employees.forEach((m) => (m.firstName = "nnn"));

const { data: products } = await useFetch("https://fakestoreapi.com/products");
console.log(products);
</script>

<template>
	<h2 class="text-xl mb-3">{{ employees.length }} employees</h2>
	<ul>
		<li v-for="employee in employees">
			{{ employee.firstName }} {{ employee.lastName }}
		</li>
	</ul>
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
</template>

<style scoped></style>
