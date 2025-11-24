<script setup>
    import { ref } from 'vue'
	import { NotebookTabs, Minus, Coffee, CakeSlice, Croissant  } from 'lucide-vue-next'

    const header = ref('Bakery Shopping App')

	const items = ref([
		{name: "Coffee", icon: Coffee},
		{name: "Cake portion", icon: CakeSlice},
		{name: "Croissant", icon: Croissant},

	])
</script>

<template>
    <div class="min-h-screen flex justify-center items-center bg-vue/30">
		<div class="flex flex-col bg-white rounded-2xl max-w-5xl px-18 py-12 shadow-2xl">
			<div class="flex items-end justify-center gap-2.5">
				<NotebookTabs class="size-8 text-vue" />
				<h1 class="text-2xl text-slate-500">{{ header }}</h1>
			</div>
			<ul class="mt-5">
				<li
					v-for="({name, icon}) in items"
					:key="name"
					class="flex items-center gap-2"
				>
					<span>
						<Minus class="size-5 text-slate-400" />
					</span>
					<span class="text-slate-400">{{ name }}</span>
					<component :is="icon" class="size-5 text-vue/70" />
				</li>
			</ul>
		</div>
  </div>
</template>
