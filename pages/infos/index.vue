<script setup>
const route = useRoute();
useHead({
	title: "The Single Infos Page",
	description: "the description",
});
</script>

<template>
	<h1>Infos Page</h1>
	<ul class="flex gap-3 w-fit bg-slate-950 text-slate-100 p-2 rounded">
		<li><NuxtLink to="/infos/system">system infos</NuxtLink></li>
		<li><NuxtLink to="/infos/custom">custom infos</NuxtLink></li>
	</ul>
	<p>infos will be here</p>
</template>

<style scoped></style>
