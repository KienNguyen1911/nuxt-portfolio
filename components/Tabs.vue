<script setup>
const items = [{
  label: 'Sample',
  route: '/sample-page',
}, {
  label: 'Index',
  route: '/',
}, {
  label: 'Profile',
  route: '/profile',
}]
const uiCard = ref({
//   background: 'bg-white backdrop-filter backdrop-blur-md bg-opacity-70 dark:bg-slate-900 dark:backdrop-filter dark:backdrop-blur-md dark:bg-opacity-70',
    "wrapper": "relative space-y-2",
    "container": "relative w-full",
    "base": "focus:outline-none",
    "list": {
        "base": "relative",
        "background": 'bg-white backdrop-filter backdrop-blur-md bg-opacity-70 dark:bg-slate-900 dark:backdrop-filter dark:backdrop-blur-md dark:bg-opacity-70',
        "rounded": "rounded-lg",
        "shadow": "",
        "padding": "p-1",
        "height": "h-10",
        "width": "w-full",
        "marker": {
            "wrapper": "absolute top-[4px] left-[4px] duration-200 ease-out focus:outline-none",
            "base": "w-full h-full",
            "background": "bg-white dark:bg-gray-900",
            "rounded": "rounded-md",
            "shadow": "shadow-sm"
        },
        "tab": {
            "base": "relative inline-flex items-center justify-center flex-shrink-0 w-full whitespace-nowrap focus:outline-none disabled:cursor-not-allowed disabled:opacity-75 transition-colors duration-200 ease-out",
            "background": "",
            "active": "text-gray-900 dark:text-white",
            "inactive": "text-gray-500 dark:text-gray-400",
            "height": "h-8",
            "padding": "px-3",
            "size": "text-sm",
            "font": "font-medium",
            "rounded": "rounded-md",
            "shadow": ""
        }
    }
})
const route = useRoute()
const router = useRouter()
const selected = computed({
  get () {
    const index = items.findIndex((item) => item.route === route.path)
    if (index === -1) {
      return 0
    }
    return index
  },
  set (value) {
    // Hash is specified here to prevent the page from scrolling to the top
    router.push(items[value].route)
  }
})
console.log(selected)
</script>
<template lang="">
    <div>
        <UTabs :items="items" v-model="selected" :ui="uiCard" />
    </div>
</template>
<style lang="">
    
</style>