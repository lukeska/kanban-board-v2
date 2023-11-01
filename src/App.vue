<template>
	<div class="h-full">
		<TransitionRoot as="template" :show="sidebarOpen">
			<Dialog
				as="div"
				class="relative z-50 lg:hidden"
				@close="sidebarOpen = false"
			>
				<TransitionChild
					as="template"
					enter="transition-opacity ease-linear duration-300"
					enter-from="opacity-0"
					enter-to="opacity-100"
					leave="transition-opacity ease-linear duration-300"
					leave-from="opacity-100"
					leave-to="opacity-0"
				>
					<div class="fixed inset-0 bg-gray-900/80" />
				</TransitionChild>

				<div class="fixed inset-0 flex">
					<TransitionChild
						as="template"
						enter="transition ease-in-out duration-300 transform"
						enter-from="-translate-x-full"
						enter-to="translate-x-0"
						leave="transition ease-in-out duration-300 transform"
						leave-from="translate-x-0"
						leave-to="-translate-x-full"
					>
						<DialogPanel
							class="relative flex flex-1 w-full max-w-xs mr-16"
						>
							<TransitionChild
								as="template"
								enter="ease-in-out duration-300"
								enter-from="opacity-0"
								enter-to="opacity-100"
								leave="ease-in-out duration-300"
								leave-from="opacity-100"
								leave-to="opacity-0"
							>
								<div
									class="absolute top-0 flex justify-center w-16 pt-5 left-full"
								>
									<button
										type="button"
										class="-m-2.5 p-2.5"
										@click="sidebarOpen = false"
									>
										<span class="sr-only"
											>Close sidebar</span
										>
										<XMarkIcon
											class="w-6 h-6 text-white"
											aria-hidden="true"
										/>
									</button>
								</div>
							</TransitionChild>

							<div
								class="flex bg-white grow gap-y-5 ring-1 ring-white/10"
							>
								<div
									class="flex flex-col bg-gradient-to-b from-violet-600 via-indigo-700 to-indigo-900 gap-y-4"
								>
									<div
										class="flex items-center justify-center h-16 mx-2 border-b border-white/20 shrink-0"
									>
										<HeartIcon
											class="w-8 h-8 text-green-300"
										/>
									</div>
									<nav
										class="flex flex-col justify-center flex-1 px-2 w-14"
									>
										<ul
											role="list"
											class="flex-1 space-y-1"
										>
											<li
												v-for="item in navigation"
												:key="item.name"
											>
												<a
													:href="item.href"
													:class="[
														item.current
															? 'bg-white/10 text-white'
															: 'text-gray-200 hover:text-white hover:bg-white/10',
														'group flex rounded-md p-2 text-sm leading-6',
													]"
												>
													<component
														:is="item.icon"
														class="w-6 h-6 shrink-0"
														aria-hidden="true"
													/>
												</a>
											</li>
										</ul>
									</nav>
								</div>
								<Sidebar />
							</div>
						</DialogPanel>
					</TransitionChild>
				</div>
			</Dialog>
		</TransitionRoot>

		<!-- Static sidebar for desktop -->
		<div
			class="hidden lg:fixed lg:inset-y-0 lg:left-0 lg:z-50 lg:block lg:w-20 lg:overflow-y-auto lg:bg-gradient-to-b lg:from-violet-600 lg:via-indigo-700 lg:to-indigo-900 lg:pb-4"
		>
			<div class="flex items-center justify-center h-16 shrink-0">
				<HeartIcon class="w-8 h-8 text-green-300" />
			</div>
			<nav class="mt-8">
				<ul role="list" class="flex flex-col items-center space-y-1">
					<li v-for="item in navigation" :key="item.name">
						<a
							:href="item.href"
							:class="[
								item.current
									? 'bg-white/10 text-white'
									: 'text-gray-200 hover:text-white hover:bg-white/10',
								'group flex gap-x-3 rounded-md p-3 text-sm leading-6 font-semibold',
							]"
						>
							<component
								:is="item.icon"
								class="w-6 h-6 shrink-0"
								aria-hidden="true"
							/>
							<span class="sr-only">{{ item.name }}</span>
						</a>
					</li>
				</ul>
			</nav>
		</div>

		<div class="h-full lg:pl-20">
			<main class="h-full lg:pl-60">
				<div
					class="flex items-center h-16 px-4 space-x-2 bg-white border-b border-gray-200 shadow-sm sm:px-6 lg:px-8 lg:space-x-0"
				>
					<button
						type="button"
						class="-m-2.5 p-2.5 text-gray-700 lg:hidden"
						@click="sidebarOpen = true"
					>
						<span class="sr-only">Open sidebar</span>
						<Bars3Icon class="w-6 h-6" aria-hidden="true" />
					</button>

					<!-- Separator -->
					<div
						class="w-px h-6 bg-gray-900/10 lg:hidden"
						aria-hidden="true"
					/>

					<div class="flex self-stretch flex-1 gap-x-4 lg:gap-x-6">
						<form
							class="relative flex items-center flex-1"
							action="#"
							method="GET"
						>
							<label for="search-field" class="sr-only"
								>Search</label
							>
							<MagnifyingGlassIcon
								class="absolute inset-y-0 w-5 h-full text-gray-500 pointer-events-none left-3"
								aria-hidden="true"
							/>
							<input
								id="search-field"
								class="block w-full h-10 max-w-sm px-10 py-0 text-gray-900 border border-indigo-200 rounded-lg bg-slate-50 placeholder:text-gray-400 focus:ring-0 sm:text-sm"
								placeholder="Search..."
								type="search"
								name="search"
							/>
						</form>
						<div class="flex items-center gap-x-4 lg:gap-x-6">
							<button
								type="button"
								class="-m-2.5 p-2.5 text-gray-400 hover:text-gray-500"
							>
								<span class="sr-only">View notifications</span>
								<BellIcon class="w-6 h-6" aria-hidden="true" />
							</button>

							<button
								type="button"
								class="-m-2.5 p-2.5 text-gray-400 hover:text-gray-500"
							>
								<span class="sr-only">View statistics</span>
								<ChartBarIcon
									class="w-6 h-6"
									aria-hidden="true"
								/>
							</button>

							<!-- Separator -->
							<div
								class="hidden lg:block lg:h-6 lg:w-px lg:bg-gray-900/10"
								aria-hidden="true"
							/>

							<!-- Profile dropdown -->
							<Menu as="div" class="relative">
								<MenuButton
									class="-m-1.5 flex items-center p-1.5"
								>
									<span class="sr-only">Open user menu</span>
									<img
										class="w-8 h-8 rounded-full bg-gray-50"
										src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
										alt=""
									/>
									<span
										class="hidden lg:flex lg:items-center"
									>
										<span
											class="ml-4 text-sm font-semibold leading-6 text-gray-900"
											aria-hidden="true"
											>Tom Cook</span
										>
										<ChevronDownIcon
											class="w-5 h-5 ml-2 text-gray-400"
											aria-hidden="true"
										/>
									</span>
								</MenuButton>
								<transition
									enter-active-class="transition duration-100 ease-out"
									enter-from-class="transform scale-95 opacity-0"
									enter-to-class="transform scale-100 opacity-100"
									leave-active-class="transition duration-75 ease-in"
									leave-from-class="transform scale-100 opacity-100"
									leave-to-class="transform scale-95 opacity-0"
								>
									<MenuItems
										class="absolute right-0 z-10 mt-2.5 w-32 origin-top-right rounded-md bg-white py-2 shadow-lg ring-1 ring-gray-900/5 focus:outline-none"
									>
										<MenuItem
											v-for="item in userNavigation"
											:key="item.name"
											v-slot="{ active }"
										>
											<a
												:href="item.href"
												:class="[
													active ? 'bg-gray-50' : '',
													'block px-3 py-1 text-sm leading-6 text-gray-900',
												]"
												>{{ item.name }}</a
											>
										</MenuItem>
									</MenuItems>
								</transition>
							</Menu>
						</div>
					</div>
				</div>

				<div class="h-full">
					<Project />
				</div>
			</main>
		</div>

		<aside
			class="fixed top-0 hidden h-full overflow-y-auto border-r border-gray-200 left-20 w-60 lg:block"
		>
			<!-- Secondary column (hidden on smaller screens) -->
			<Sidebar />
		</aside>
	</div>
</template>

<script setup>
import Subnav from "./components/Subnav.vue";
import Sidebar from "./components/Sidebar.vue";
import { ref } from "vue";
import {
	Dialog,
	DialogPanel,
	Menu,
	MenuButton,
	MenuItem,
	MenuItems,
	TransitionChild,
	TransitionRoot,
} from "@headlessui/vue";
import {
	Bars3Icon,
	BellIcon,
	ChartBarIcon,
	CalendarIcon,
	ChartPieIcon,
	DocumentDuplicateIcon,
	FolderIcon,
	HomeIcon,
	UsersIcon,
	XMarkIcon,
} from "@heroicons/vue/24/outline";
import {
	ChevronDownIcon,
	MagnifyingGlassIcon,
	FunnelIcon,
	Bars3BottomRightIcon,
	HeartIcon,
} from "@heroicons/vue/20/solid";
import Project from "./components/Project.vue";

const navigation = [
	{ name: "Dashboard", href: "#", icon: HomeIcon, current: true },
	{ name: "Team", href: "#", icon: UsersIcon, current: false },
	{ name: "Projects", href: "#", icon: FolderIcon, current: false },
	{ name: "Calendar", href: "#", icon: CalendarIcon, current: false },
	{
		name: "Documents",
		href: "#",
		icon: DocumentDuplicateIcon,
		current: false,
	},
	{ name: "Reports", href: "#", icon: ChartPieIcon, current: false },
];
const userNavigation = [
	{ name: "Your profile", href: "#" },
	{ name: "Sign out", href: "#" },
];

const sidebarOpen = ref(true);
</script>
