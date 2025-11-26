<script setup>
    import { ref } from 'vue'
	import { NotebookTabs, Minus, Coffee, CakeSlice, Croissant, SmilePlus  } from 'lucide-vue-next'

    const header = ref('Bakery Shopping App')

	const items = ref([
		{name: "Coffee", icon: Coffee},
		{name: "Cake portion", icon: CakeSlice},
		{name: "Croissant", icon: Croissant},
	])

    const newItem = ref("")
    const newItemHighPriority = ref(false)

    const saveItem = () => {
        if (newItem.value.trim()) {
            items.value.push({
                id: items.value.length + 1,
                name: newItem.value,
                icon: SmilePlus,
                highPriority: newItemHighPriority.value
            })
            // Reset
            newItem.value = ''
            newItemHighPriority.value = false
        }
    }
</script>

<template>
    <div class="min-h-screen flex justify-center items-center bg-vue/30">
		<div class="flex flex-col bg-white border-2 border-slate-600 rounded-2xl max-w-5xl px-18 py-12 shadow-2xl">
			<div class="flex items-end justify-center gap-2.5 mb-6">
				<NotebookTabs class="size-8 text-vue" />
				<h1 class="text-2xl text-slate-500">{{ header }}</h1>
			</div>
            <form @submit.prevent="saveItem">
                <input
                    v-model.trim="newItem"
                    type="text"
                    class="border border-slate-400 mt-4 p-2.5 rounded-2xl text-xs"
                    placeholder="Add an product..."
                />
                <div class="my-4 flex justify-between items-center">
                    <div class="flex gap-2">
                        <input
                            v-model="newItemHighPriority"
                            type="checkbox"
                            class="w-4 h-4 rounded border accent-vue focus:outline-none"
                            @click="$event.target.blur()"
                        />
                        <span class="text-sm font-bold">High Priority</span>
                    </div>
                    <button
                        class="btn-sm bg-vue px-3 py-1.5 rounded text-white"
                    >
                        Save Item
                    </button>
                </div>
            </form>
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
