<script setup>
import users from "../../data/users.json";
console.log(users);
const route = useRoute();
const id = Number(route.params.id);
const user = users.find((m) => m.employeeID === id);
</script>

<template>
	<NuxtLayout name="highlight">
		<p class="font-semibold">{{ user.firstName }} {{ user.lastName }}</p>
		<p class="w-[20rem] text-blue-950 italic">{{ user.notes }}</p>
	</NuxtLayout>
</template>

<style scoped></style>
