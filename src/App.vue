<template>
	<div class="kanban">
		<h1>Kanban</h1>
		<div class="columns-container">
			<div v-for="column in columns" :key="column.id" class="column"></div>
		</div>
	</div>
</template>

<script setup lang="ts">
import { ref } from "vue";

interface Card {
	id: number;
	text: string;
}

interface Column {
	id: number;
	title: string;
	cards: Card[];
}

const columns = ref<Column[]>([
	{
		id: 1,
		title: "To Do",
		cards: [
			{ id: 101, text: "Design the login page." },
			{ id: 102, text: "Setup the database schema." },
		],
	},
	{
		id: 2,
		title: "In Progress",
		cards: [{ id: 201, text: "Develop the API endpoints." }],
	},
	{
		id: 3,
		title: "Done",
		cards: [{ id: 301, text: "Initialize the Vue project." }],
	},
]);
</script>

<style scoped></style>
