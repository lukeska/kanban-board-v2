<script setup>
import Ticket from "./Ticket.vue";
import { ref } from "vue";

const lanes = ref([
	{
		name: "Upcoming",
		budget: "$500",
		color: "#75a0ff",
		tickets: [
			{
				title: "We don't have a brig. Meh.",
				description:
					"Calculon is gonna kill us and it's all everybody else's fault!",
				created_at: "21 Sep",
				links: 2,
				comments: 12,
				completion: 50,
				labels: ["Design", "Development"],
				tasks: [
					{ done: false, task: "Define testing objectives" },
					{ done: true, task: "Prepare tests scenarios" },
				],
			},
			{
				title: "You are the last hope of the universe.",
				description: "Stop! Don't shoot fire stick in space canoe!",
				created_at: "19 Sep",
				links: 2,
				comments: 1,
				completion: 0,
				labels: ["UI/UX"],
			},
		],
	},
	{
		name: "In Progress",
		budget: "$1500",
		color: "#c275ff",
		tickets: [
			{
				title: "Update favicon",
				description:
					"Update the website's icon to enhance visual identification.",
				created_at: "21 Sep",
				links: 2,
				comments: 12,
				completion: 75,
				labels: ["Design", "Development"],
				tasks: [
					{ done: true, task: "Create SVG file" },
					{ done: true, task: "Create PNG file" },
					{ done: false, task: "Create ICO file" },
				],
				img: "/kanban-board-v2/screenshot.jpg",
			},
		],
	},
	{
		name: "In Review",
		budget: "$1500",
		color: "#fec775",
		tickets: [
			{
				title: "Usability Testing",
				description:
					"Conduct comprehensive usability testing to enhance user experience.",
				created_at: "10 Sep",
				links: 4,
				comments: 2,
				completion: 95,
				labels: ["UX Research", "+3"],
				tasks: [
					{ done: true, task: "Define testing objectives" },
					{ done: true, task: "Prepare test scenarios" },
					{ done: true, task: "Execute usability testing" },
				],
			},
		],
	},
	{
		name: "Ready",
		budget: "$1500",
		color: "#57e06c",
		tickets: [
			{
				title: "Call with Fry",
				description:
					"Schedule a call with the product manager to present the project.",
				created_at: "10 Sep",
				links: 2,
				comments: 2,
				completion: 100,
				labels: ["Meeting"],
			},
			{
				title: "Mood boards",
				description:
					"Create 2 mood boards for the redesign of the current site.",
				created_at: "10 Sep",
				links: 12,
				comments: 29,
				completion: 100,
				labels: ["Design", "Development"],
			},
		],
	},
]);
</script>

<template>
	<div class="flex space-x-6 overflow-x-scroll snap-x snap-mandatory">
		<div
			v-for="lane in lanes"
			:key="lane.name"
			class="w-[250px] shrink-0 snap-start"
		>
			<div class="flex justify-between px-1 mb-4">
				<div>
					<span
						class="inline-block w-2 h-2 mr-2 rounded-full"
						:style="'background-color:' + lane.color"
					></span>
					<span>{{ lane.name }}</span>
					<span class="ml-3 text-gray-400">{{
						lane.tickets.length
					}}</span>
				</div>
				<div>{{ lane.budget }}</div>
			</div>
			<div class="space-y-4">
				<Ticket v-for="ticket in lane.tickets" :ticket="ticket" />
			</div>
			<div>
				<button
					class="w-full py-2 mt-4 text-center transition bg-gray-100 border rounded-lg border-zinc-300 text-zinc-600 hover:shadow hover:bg-white"
				>
					+ Add Task
				</button>
			</div>
		</div>
	</div>
</template>
