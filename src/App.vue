<template>
	<div class="kanban">
		<h1>Kanban</h1>
		<div class="columns-container">
			<div v-for="column in columns" :key="column.id" class="column">
				<h2>{{ column.title }}</h2>
				<div class="cards">
					<div v-for="card in column.cards" :key="card.id" class="card">
						{{ card.text }}
					</div>
				</div>
			</div>
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

<style scoped>
.kanban {
	min-height: 100vh;
	background-color: #1a1a1a;
	color: #ffffff;
	padding: 2rem;
}

h1 {
	color: #ffffff;
	margin-bottom: 2rem;
	font-size: 2.5rem;
	font-weight: 600;
}

.columns-container {
	display: flex;
	gap: 2rem;
	align-items: flex-start;
}

.column {
	background-color: #2d2d2d;
	border-radius: 8px;
	padding: 1.5rem;
	min-width: 300px;
	flex: 1;
}

.column h2 {
	color: #ffffff;
	margin-bottom: 1rem;
	font-size: 1.25rem;
	font-weight: 500;
}

.cards {
	display: flex;
	flex-direction: column;
	gap: 1rem;
}

.card {
	background-color: #3d3d3d;
	border-radius: 6px;
	padding: 1rem;
	color: #ffffff;
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
	transition:
		transform 0.2s ease,
		box-shadow 0.2s ease;
}

.card:hover {
	transform: translateY(-2px);
	box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
}
</style>
