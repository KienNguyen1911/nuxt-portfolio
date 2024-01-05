<template lang="">
  <UContainer :ui="uiContainer" >
    <Tabs />
    <UCard :ui="uiCard">
      <slot />
  
      <div class="btn-mode">
        <ClientOnly>
          <UToggle 
            variant="ghost"
            aria-label="Theme"
            off-icon="i-heroicons-moon-20-solid"
            on-icon="i-heroicons-sun-20-solid"
            @click="isDark = !isDark"
            v-model="toggle"
          />
          <template #fallback>
            <div class="w-8 h-8" />
          </template>
        </ClientOnly>
      </div>

    </UCard>
  </UContainer>
</template>
<script setup>
const uiCard = ref({
  background: 'bg-white backdrop-filter backdrop-blur-md bg-opacity-70 dark:bg-slate-900 dark:backdrop-filter dark:backdrop-blur-md dark:bg-opacity-70',
})
const uiContainer = ref({
  "base": "mx-auto",
  "padding": "px-4 sm:px-6 lg:px-8 py-3",
  "constrained": "max-w-7xl"
})

const toggle = ref(false)

const colorMode = useColorMode()
const isDark = computed({
  get () {
    return colorMode.value === 'dark'
  },
  set () {
    colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark'
  }
})
</script>
<style >
.btn-mode {
  position: absolute;
  bottom: 1.5rem;
  right: 1.5rem;
}
</style>