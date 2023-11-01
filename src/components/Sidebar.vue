<script setup>
import Subnav from "./Subnav.vue";
import { Bars3BottomRightIcon } from "@heroicons/vue/20/solid";
</script>

<template>
	<div class="flex-1 overflow-hidden">
		<div
			class="flex items-center h-16 px-5 border-b border-gray-200 shadow-sm"
		>
			<div
				class="flex items-center justify-between w-full text-lg font-semibold"
			>
				<span>All Projects</span>
				<button class="p-1 rounded bg-slate-300">
					<Bars3BottomRightIcon
						class="w-4 h-4 text-white"
						aria-hidden="true"
					/>
				</button>
			</div>
		</div>
		<div class="h-full overflow-y-auto">
			<div class="px-5 py-5">
				<Subnav />
			</div>
		</div>
	</div>
</template>
