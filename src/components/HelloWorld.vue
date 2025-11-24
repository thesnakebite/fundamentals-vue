<script setup>
    import { ref } from 'vue'

    const msg = ref('Hello World!')
</script>

<template>
    <div class="min-h-screen flex justify-center items-center bg-vue/30">
		<div class="flex flex-col bg-white rounded-2xl max-w-5xl px-18 py-12 shadow-2xl">
			<h1 class="text-2xl text-vue">{{ msg.toLocaleUpperCase() }}</h1>
			<h3 class="text-sm text-slate-400">
				You’ve successfully created a project with
				<a href="https://vite.dev/" target="_blank" rel="noopener" class="text-slate-600">Vite</a> +
				<a href="https://vuejs.org/?uwu=true" target="_blank" rel="noopener" class="text-vue">Vue 3</a>.
			</h3>
			<div class="mt-5">
				<input type="text" v-model="msg" class="border-2 px-2.5 py-1.5 shadow-2xl rounded-2xl">
			</div>
		</div>
  </div>
</template>
