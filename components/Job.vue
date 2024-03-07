<script setup>
defineProps({
	job: {
		type: Object,
		required: true,
	},
});
</script>

<template>
		<slot name="before" />
	<input type="checkbox" :checked="job.skillList.includes('react')" />
	{{ job.title }}
	<div>
		<h2>Extra Information</h2>
		<slot name="after"/>
	</div>
</template>
