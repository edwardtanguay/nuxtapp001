<script setup>
import axios from "axios";
import Jobs from './components/Jobs';

let jobs = ref([]);

const numberOfReactJobs = computed(() => {
	return jobs.value.filter((m) => m.skillList.includes("react")).length;
});

const fetchData = async () => {
	const response = await axios.get(
		"https://edwardtanguay.vercel.app/share/jobs.json"
	);
	jobs.value = response.data;
};
</script>

<template>
	<div>
		<h1 class="text-3xl mb-3">Info Site</h1>
		<img src="/jobs.png" class="w-[24rem] rounded-lg" />
		<button @click="fetchData" class="mb-3">fetch data</button>
		<h2 class="text-xl mb-3" v-if="jobs.length > 0">
			checked = React ({{ numberOfReactJobs }})
		</h2>
		<ul class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-2">
			<Jobs :jobs="jobs"/>
		</ul>
	</div>
</template>

<style lang="scss">
$main_color: orange;

h1 {
	color: $main_color;
}
</style>
