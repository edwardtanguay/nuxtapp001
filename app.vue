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
</script>

<template>
	<div>
		<h1 class="text-3xl mb-3">Info Site</h1>
		<img src="/jobs.png" class="w-[24rem] rounded-lg mb-3" />
		<button @click="fetchData" class="mb-3">fetch data</button>
		<h2 class="text-xl mb-3" v-if="jobs.length > 0">
			checked = React ({{ numberOfReactJobs }})
		</h2>
		<ul>
			<li v-for="job in jobs" :key="job.id">
				<input
					type="checkbox"
					:checked="job.skillList.includes('react')"
				/>
				{{ job.title }}
			</li>
		</ul>
	</div>
</template>
