<script setup>
const props = defineProps({
	jobs: {
		type: Array,
		required: true,
	},
});
const { jobs } = props;
</script>

<template>
	<li v-for="job in jobs" :key="job.id">
		<input type="checkbox" :checked="job.skillList.includes('react')" />
		{{ job.title }}
	</li>
</template>

<style scoped></style>
