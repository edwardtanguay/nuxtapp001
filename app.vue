<script>
import { defineNuxtComponent } from "#app";
import axios from "axios";

export default defineNuxtComponent({
	data: () => ({
		jobs: [],
	}),
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
		<h1>Info Site</h1>
		<img src="/jobs.png" />
		<button @click="fetchData">fetch data</button>
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
