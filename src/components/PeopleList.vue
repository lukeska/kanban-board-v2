<script setup>
defineProps({
	size: Number,
});
</script>

<template>
	<div class="flex -space-x-2">
		<div>
			<img
				class="rounded-full outline outline-2 outline-white"
				:class="size ?? 'w-8 h-8'"
				src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
				alt=""
			/>
		</div>
		<div>
			<img
				class="rounded-full outline outline-2 outline-white"
				:class="size ?? 'w-8 h-8'"
				src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
				alt=""
			/>
		</div>
		<div
			class="flex items-center justify-center text-sm leading-none text-white bg-indigo-500 rounded-full outline outline-2 outline-white"
			:class="size ?? 'w-8 h-8'"
		>
			<span>+4</span>
		</div>
	</div>
</template>
