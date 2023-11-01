<script setup>
import ProjectHeader from "./ProjectHeader.vue";
import KanbanBoard from "./KanbanBoard.vue";
import { Menu, MenuButton, MenuItems, MenuItem } from "@headlessui/vue";
import {
	ChevronDownIcon,
	Bars3BottomRightIcon,
	ArrowUturnDownIcon,
	ArrowUturnUpIcon,
	AdjustmentsHorizontalIcon,
	TableCellsIcon,
	ListBulletIcon,
	CalendarIcon,
	LinkIcon,
	ChatBubbleLeftIcon,
	EllipsisVerticalIcon,
	EllipsisHorizontalIcon,
} from "@heroicons/vue/20/solid";
import PeopleList from "./PeopleList.vue";
</script>
<template>
	<div class="h-full">
		<ProjectHeader
			class="px-4 py-10 sm:px-6 lg:px-8 lg:py-6"
		></ProjectHeader>

		<div
			class="flex flex-col items-start justify-between px-4 md:flex-row sm:px-6 lg:px-8"
		>
			<div class="flex pt-2 space-x-2 md:space-x-4">
				<a
					href="#"
					class="relative inline-block px-2 pb-4 overflow-hidden text-gray-500 shrink-0 hover:text-black after:transition-all after:w-full after:h-2 after:bg-gray-300 after:absolute after:-bottom-2 hover:after:bottom-0 after:left-0 after:rounded-t-md after:scale-50 hover:after:scale-100 after:opacity-0 hover:after:opacity-100"
					>Overview
				</a>
				<a
					href="#"
					class="relative inline-block px-2 pb-4 shrink-0 after:w-full after:h-2 after:bg-indigo-600 after:block after:absolute after:bottom-0 after:left-0 after:rounded-t-md"
					>Tasks
				</a>
				<a
					href="#"
					class="relative inline-block px-2 pb-4 overflow-hidden text-gray-500 shrink-0 hover:text-black after:transition-all after:w-full after:h-2 after:bg-gray-300 after:absolute after:-bottom-2 hover:after:bottom-0 after:left-0 after:rounded-t-md after:scale-50 hover:after:scale-100 after:opacity-0 hover:after:opacity-100"
					>Notes
					<span
						class="inline-flex justify-center w-5 h-5 text-sm leading-tight text-white bg-red-400 rounded-full"
						>2</span
					></a
				>
				<a
					href="#"
					class="relative inline-block px-2 pb-4 overflow-hidden text-gray-500 shrink-0 hover:text-black after:transition-all after:w-full after:h-2 after:bg-gray-300 after:absolute after:-bottom-2 hover:after:bottom-0 after:left-0 after:rounded-t-md after:scale-50 hover:after:scale-100 after:opacity-0 hover:after:opacity-100"
					>Questions
				</a>
			</div>
			<div
				class="flex w-full py-2 space-x-3 border-t border-gray-200 md:w-auto md:py-0 md:border-0"
			>
				<Menu as="div" class="relative inline-block text-left">
					<div>
						<MenuButton
							class="inline-flex justify-center w-full px-3 py-2 text-sm font-medium rounded-md bg-violet-50 text-violet-950 hover:bg-opacity-30 focus:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-opacity-75"
						>
							Sort by
							<ChevronDownIcon
								class="w-5 h-5 ml-2 -mr-1 text-violet-950"
								aria-hidden="true"
							/>
						</MenuButton>
					</div>

					<transition
						enter-active-class="transition duration-100 ease-out"
						enter-from-class="transform scale-95 opacity-0"
						enter-to-class="transform scale-100 opacity-100"
						leave-active-class="transition duration-75 ease-in"
						leave-from-class="transform scale-100 opacity-100"
						leave-to-class="transform scale-95 opacity-0"
					>
						<MenuItems
							class="absolute right-0 w-56 mt-2 origin-top-right bg-white divide-y divide-gray-100 rounded-md shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none"
						>
							<div class="px-1 py-1">
								<MenuItem v-slot="{ active }">
									<button
										:class="[
											active
												? 'bg-violet-500 text-white'
												: 'text-gray-900',
											'group flex w-full items-center rounded-md px-2 py-2 text-sm',
										]"
									>
										<ArrowUturnDownIcon
											:active="active"
											class="w-5 h-5 mr-2 text-violet-400 group-hover:text-white"
											aria-hidden="true"
										/>
										Descending
									</button>
								</MenuItem>
								<MenuItem v-slot="{ active }">
									<button
										:class="[
											active
												? 'bg-violet-500 text-white'
												: 'text-gray-900',
											'group flex w-full items-center rounded-md px-2 py-2 text-sm',
										]"
									>
										<ArrowUturnUpIcon
											:active="active"
											class="w-5 h-5 mr-2 text-violet-400 group-hover:text-white"
											aria-hidden="true"
										/>
										Ascending
									</button>
								</MenuItem>
							</div>
						</MenuItems>
					</transition>
				</Menu>

				<Menu as="div" class="relative inline-block text-left">
					<div>
						<MenuButton
							class="inline-flex justify-center w-full px-3 py-2 text-sm font-medium rounded-md bg-violet-50 text-violet-950 hover:bg-opacity-30 focus:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-opacity-75"
						>
							Filter
							<ChevronDownIcon
								class="w-5 h-5 ml-2 -mr-1 text-violet-950"
								aria-hidden="true"
							/>
						</MenuButton>
					</div>

					<transition
						enter-active-class="transition duration-100 ease-out"
						enter-from-class="transform scale-95 opacity-0"
						enter-to-class="transform scale-100 opacity-100"
						leave-active-class="transition duration-75 ease-in"
						leave-from-class="transform scale-100 opacity-100"
						leave-to-class="transform scale-95 opacity-0"
					>
						<MenuItems
							class="absolute right-0 w-56 mt-2 origin-top-right bg-white divide-y divide-gray-100 rounded-md shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none"
						>
							<div class="px-1 py-1">
								<MenuItem v-slot="{ active }">
									<button
										:class="[
											active
												? 'bg-violet-500 text-white'
												: 'text-gray-900',
											'group flex w-full items-center rounded-md px-2 py-2 text-sm',
										]"
									>
										<ArrowUturnDownIcon
											:active="active"
											class="w-5 h-5 mr-2 text-violet-400 group-hover:text-white"
											aria-hidden="true"
										/>
										Descending
									</button>
								</MenuItem>
								<MenuItem v-slot="{ active }">
									<button
										:class="[
											active
												? 'bg-violet-500 text-white'
												: 'text-gray-900',
											'group flex w-full items-center rounded-md px-2 py-2 text-sm',
										]"
									>
										<ArrowUturnUpIcon
											:active="active"
											class="w-5 h-5 mr-2 text-violet-400 group-hover:text-white"
											aria-hidden="true"
										/>
										Ascending
									</button>
								</MenuItem>
							</div>
						</MenuItems>
					</transition>
				</Menu>

				<div class="flex items-center">
					<span class="block w-px h-8 bg-violet-300"></span>
				</div>

				<div
					class="flex items-center px-3 py-2 space-x-2 text-sm font-medium rounded-md bg-violet-50 text-violet-700"
				>
					<button>
						<TableCellsIcon class="w-5 h-5" />
					</button>
					<button class="text-violet-300 hover:text-violet-700">
						<ListBulletIcon class="w-5 h-5" />
					</button>
				</div>
			</div>
		</div>
		<div
			class="p-4 pr-0 border-t border-gray-200 md:p-10 md:pr-0 bg-slate-100"
		>
			<KanbanBoard />
		</div>
	</div>
</template>
