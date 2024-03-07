<script setup>
import users from "../../data/users.json";
</script>

<template>
	<h2 class="text-xl mb-3">All Users</h2>
	<ul class="list-disc ml-6">
		<li v-for="user in users" class="mb-3" :key="user.employeeID">
			<div class="font-semibold underline"><NuxtLink :to="`/users/${user.employeeID}`">{{ user.firstName }} {{ user.lastName }}</NuxtLink></div>
		</li>
	</ul>
</template>

<style scoped></style>
