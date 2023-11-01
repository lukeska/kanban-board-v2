<template>
	<div
		class="flex flex-col justify-between w-full space-y-4 md:items-center md:flex-row md:space-y-0"
	>
		<div>
			<div class="flex items-center space-x-10">
				<div class="flex items-center space-x-3">
					<div class="p-1.5 w-7 h-7 bg-violet-200 rounded-full">
						<GlobeAmericasIcon
							class="w-4 h-4 text-indigo-900 shrink-0"
							aria-hidden="true"
						/>
					</div>
					<h1 class="text-xl font-semibold">Global Agency</h1>
					<button>
						<PencilSquareIcon class="w-5 h-5 text-gray-300" />
					</button>
				</div>
				<div class="flex items-center space-x-2">
					<div class="w-12 h-2 rounded-full bg-violet-100 xl:w-52">
						<div
							class="h-2 rounded-full bg-gradient-to-r from-violet-400 to-indigo-700"
							style="width: 67%"
						></div>
					</div>
					<div class="text-sm text-gray-400">
						67% <span class="hidden xl:inline">completed</span>
					</div>
				</div>
			</div>
			<div
				class="relative flex pt-4 pl-10 space-x-2 text-sm text-gray-400 before:border-b before:border-l before:border-gray-300 before:rounded-bl-lg before:left-3 before:top-2 before:absolute before:w-5 before:h-5"
			>
				<a href="#">iOS App</a>
				<span>/</span>
				<a href="#">Android App</a>
				<span>/</span>
				<span class="text-gray-800">Website</span>
			</div>
		</div>

		<div
			class="flex items-center py-2 space-x-5 border-t border-b md:border-0 md:py-0"
		>
			<PeopleList />
			<div>
				<button
					class="flex items-center px-5 py-3 space-x-2 bg-green-300 rounded-lg"
				>
					<ShareIcon class="w-6 h-6" />
					<span class="hidden xl:inline">Share workspace</span>
				</button>
			</div>
		</div>
	</div>
</template>

<script setup>
import {
	ChevronDownIcon,
	MagnifyingGlassIcon,
	FunnelIcon,
	Bars3BottomRightIcon,
	Bars3Icon,
	BellIcon,
	CalendarIcon,
	ChartPieIcon,
	DocumentDuplicateIcon,
	FolderIcon,
	HomeIcon,
	UsersIcon,
	XMarkIcon,
	PencilSquareIcon,
	ShareIcon,
	GlobeAmericasIcon,
} from "@heroicons/vue/20/solid";
import PeopleList from "./PeopleList.vue";
</script>
