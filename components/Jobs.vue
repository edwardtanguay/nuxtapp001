<script setup>
import axios from "axios";
import Job from './Job';

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
	<button @click="fetchData" class="mb-3">fetch data</button>
	<h2 class="text-xl mb-3" v-if="jobs.length > 0">
		checked = React ({{ numberOfReactJobs }})
	</h2>
	<ul class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-2">
		<li v-for="job in jobs" :key="job.id">
		<Job :job="job"/>
		</li>
	</ul>
</template>

<style scoped></style>
