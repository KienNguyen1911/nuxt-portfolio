<script setup>
import { useMouse, useDark, useTitle } from '@vueuse/core'

// practice using composables
const { sayHello } = useUtils();
sayHello();

// practice using composable with VueUse
const { x, y } = useMouse();
const isDark = useDark()
console.log(isDark);

useTitle(() => isDark.value ? '🌙 Good evening!' : '☀️ Good morning!')
watch(isDark, () => {
  useTitle().value = isDark.value ? '🌙 Good evening!' : '☀️ Good morning!'
    console.log(useTitle().value);
})

const data = ref(null);
const error = ref(null);

const apiUrl = "https://api.sampleapis.com/codingresources/codingResources";

fetch(apiUrl)
    .then((res) => res.json())
    .then((json) => (data.value = json))
    .catch((err) => (error.value = err));
</script>

<template>
    <h1 class="text-3xl font-bold text-green-500">Sample Page</h1>
    <p>Mouse position: {{ x }}, {{ y }}</p>
    <h2>{{ useTitle() }}</h2>
    <div v-if="error">Oops! Error encountered: {{ error.message }}</div>
    <div v-else-if="data" class="data-contain">
        Data loaded:
        <pre>{{ data }}</pre>
    </div>
    <div v-else>Loading...</div>
</template>

<style scoped>
.data-contain {
    max-height: 300px;
    overflow-y: scroll;
    border: 1px solid #ccc;
    margin: 20px 0 40px;
}
</style>