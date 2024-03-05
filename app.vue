<script>
import { defineNuxtComponent } from "#app";
import axios from "axios";

export default defineNuxtComponent({
	data: () => ({
		jobs: [],
	}),
	computed: {
		numberOfReactJobs() {
			return this.jobs.filter(m => m.skillList.includes('react')).length;
		}
	},
	methods: {
		async fetchData() {
			const response = await axios.get(
				"https://edwardtanguay.vercel.app/share/jobs.json"
			);
			this.jobs = response.data;
		},
	},
});
</script>

<template>
	<div>
		<h1 class="text-3xl mb-3">Info Site</h1>
		<img src="/jobs.png" class="w-[24rem] rounded-lg mb-3" />
		<button @click="fetchData" class="mb-3">fetch data</button>
		<h2 class="text-xl mb-3" v-if="jobs.length > 0">checked = React ({{ numberOfReactJobs }})</h2>
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
