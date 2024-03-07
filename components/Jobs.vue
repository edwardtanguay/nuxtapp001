<script setup>
import axios from "axios";

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

// onMounted(() => {
// 	alert("loading...");
// });
</script>

<template>
	<button @click="fetchData" class="mb-3">fetch data</button>
	<h2 class="text-xl mb-3" v-if="jobs.length > 0">
		checked = React ({{ numberOfReactJobs }})
	</h2>
	<ul class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-2">
		<li v-for="job in jobs" :key="job.id">
			<Job :job="job">
				<template #before>
					<div class="font-bold">Info Area:</div>
				</template>
				<template #after>
					<div
						v-if="job.skillList.includes('react')"
						class="text-red-700"
					>
						job requires React
					</div>
					<div
						v-if="!job.skillList.includes('react')"
						class="italic text-blue-900"
					>
						no React necessary
					</div>
				</template>
			</Job>
		</li>
	</ul>
</template>

<style scoped></style>
