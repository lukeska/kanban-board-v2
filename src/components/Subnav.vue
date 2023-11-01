<template>
	<nav>
		<template v-for="item in navigation" :key="item.name">
			<div class="mb-4">
				<Disclosure v-slot="{ open }" defaultOpen="true">
					<DisclosureButton class="flex items-center mb-2 space-x-2">
						<ChevronDownIcon
							class="w-6 h-6 -mb-1 transition"
							:class="!open && '-rotate-90 '"
						/>
						<span v-text="item.name"></span>
						<span
							class="inline-block px-1 rounded text-stone-400 bg-slate-100"
							v-text="item.subitems.length"
						></span>
					</DisclosureButton>
					<transition
						enter-active-class="transition duration-100 ease-out"
						enter-from-class="transform scale-95 opacity-0"
						enter-to-class="transform scale-100 opacity-100"
						leave-active-class="transition duration-75 ease-out"
						leave-from-class="transform scale-100 opacity-100"
						leave-to-class="transform scale-95 opacity-0"
					>
						<DisclosurePanel>
							<ul>
								<li
									class="mb-1 -mx-2"
									v-for="subitem in item.subitems"
									:key="subitem.name"
								>
									<a
										href="#"
										class="flex items-center w-full p-2 space-x-3 transition rounded-lg hover:bg-violet-50 text-violet-950"
										:class="
											subitem.current && 'bg-violet-50'
										"
									>
										<div
											class="p-1.5 bg-violet-200 rounded-full"
										>
											<component
												:is="subitem.icon"
												class="w-4 h-4 text-indigo-900 shrink-0"
												aria-hidden="true"
											/>
										</div>
										<span
											v-text="subitem.name"
											class="flex-1"
										></span>
										<span
											v-if="subitem.unread"
											v-text="subitem.unread"
											class="flex items-center justify-center w-6 h-6 mx-0 text-white rounded-full bg-rose-400"
										></span>
									</a>
								</li>
							</ul>
						</DisclosurePanel>
					</transition>
				</Disclosure>
			</div>
		</template>
	</nav>
</template>

<script setup>
import { Disclosure, DisclosureButton, DisclosurePanel } from "@headlessui/vue";

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
	GlobeAmericasIcon,
	BuildingOffice2Icon,
} from "@heroicons/vue/20/solid";

const navigation = [
	{
		name: "Favourite",
		subitems: [
			{
				name: "Farmatic",
				href: "#",
				icon: HomeIcon,
				current: false,
				unread: null,
			},
			{
				name: "Eco Car",
				href: "#",
				icon: UsersIcon,
				current: false,
				unread: null,
			},
			{
				name: "Sport Travel",
				href: "#",
				icon: FolderIcon,
				current: false,
				unread: null,
			},
			{
				name: "Global Agency",
				href: "#",
				icon: GlobeAmericasIcon,
				current: true,
				unread: 3,
			},
			{
				name: "Skyline",
				href: "#",
				icon: BuildingOffice2Icon,
				current: false,
				unread: null,
			},
		],
	},
	{
		name: "Main Projects",
		subitems: [
			{
				name: "Dashboard",
				href: "#",
				icon: HomeIcon,
				current: false,
				unread: null,
			},
			{
				name: "Team",
				href: "#",
				icon: UsersIcon,
				current: false,
				unread: null,
			},
			{
				name: "Projects",
				href: "#",
				icon: FolderIcon,
				current: false,
				unread: null,
			},
			{
				name: "Calendar",
				href: "#",
				icon: CalendarIcon,
				current: false,
				unread: null,
			},
			{
				name: "Reports",
				href: "#",
				icon: ChartPieIcon,
				current: false,
				unread: null,
			},
		],
	},
];
</script>
