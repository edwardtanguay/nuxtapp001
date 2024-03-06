<script setup>
const props = defineProps({
	job: {
		type: Object,
		required: true,
	},
});
const { job } = props;
</script>

<template>
	<input type="checkbox" :checked="job.skillList.includes('react')" />
	{{ job.title }}
</template>

<style scoped></style>
