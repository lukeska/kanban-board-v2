<script setup>
import PeopleList from "./PeopleList.vue";
import {
	CalendarIcon,
	LinkIcon,
	ChatBubbleLeftIcon,
	EllipsisHorizontalIcon,
	CheckIcon,
} from "@heroicons/vue/20/solid";

const props = defineProps({
	ticket: Object,
});
</script>

<template>
	<div class="space-y-2">
		<div class="p-3 bg-white border rounded border-slate-300">
			<div class="flex justify-between">
				<div class="space-x-2">
					<span
						v-for="label in ticket.labels"
						:key="label"
						class="inline-block px-2 py-1 text-xs rounded bg-indigo-50"
						>{{ label }}</span
					>
				</div>
				<div>
					<button>
						<EllipsisHorizontalIcon
							class="w-8 h-8 text-gray-300 hover:text-gray-600"
						/>
					</button>
				</div>
			</div>
			<div class="mt-2 mb-2 text-lg font-semibold">
				{{ ticket.title }}
			</div>
			<div class="text-gray-500">
				{{ ticket.description }}
			</div>

			<div v-if="ticket.img">
				<img
					:src="ticket.img"
					alt=""
					class="my-2 border rounded border-slate-300"
				/>
			</div>

			<div v-if="ticket.tasks">
				<ul class="my-3 space-y-1">
					<li
						v-for="task in ticket.tasks"
						class="flex items-center space-x-2"
					>
						<div
							v-if="task.done"
							class="inline-flex items-center justify-center w-4 h-4 text-white bg-indigo-600 rounded-full"
						>
							<CheckIcon class="w-3 h-3" />
						</div>
						<div
							v-if="!task.done"
							class="inline-block w-4 h-4 border border-gray-300 rounded-full"
						></div>
						<p>{{ task.task }}</p>
					</li>
				</ul>
			</div>

			<div class="mt-4 space-y-2">
				<div class="flex justify-between">
					<span>Task progress</span>
					<span>{{ ticket.completion }}%</span>
				</div>
				<div class="w-full h-2 rounded-full bg-violet-100">
					<div
						class="h-2 rounded-full bg-gradient-to-r from-violet-400 to-indigo-700"
						:style="'width:' + ticket.completion + '%'"
					></div>
				</div>
			</div>
		</div>
		<div
			class="flex items-center justify-between px-3 py-2 bg-white border rounded border-slate-300"
		>
			<PeopleList size="w-6 h-6" />
			<div class="space-x-2 text-xs text-gray-500">
				<div class="inline-flex items-center space-x-1">
					<CalendarIcon class="w-4 h-4 text-gray-400" />
					<span>{{ ticket.created_at }}</span>
				</div>
				<div class="inline-flex items-center space-x-1">
					<LinkIcon class="w-4 h-4 text-gray-400" />
					<span>{{ ticket.links }}</span>
				</div>
				<div class="inline-flex items-center space-x-1">
					<ChatBubbleLeftIcon class="w-4 h-4 text-gray-400" />
					<span>{{ ticket.comments }}</span>
				</div>
			</div>
		</div>
	</div>
</template>
