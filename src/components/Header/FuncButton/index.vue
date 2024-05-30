<template>
    <div class="w-[32px] h-[32px] rounded-full cursor-pointer 
                hover:shadow-md hover:bg-[--main-color] 
                transition-all duration-[var(--duration-time)]
                flex items-center justify-center
                mr-[8px]
                "
     @mouseover="hoverColor = true" 
     @mouseleave="hoverColor = false">
  <SvgIconG :name="icon" :color="hoverColor ? '#fff' : ''" class="w-[80%] h-[80%] transition-all duration-[var(--duration-time)]"></SvgIconG>
</div>
</template>

<script setup lang='ts'>
import { withDefaults , ref } from 'vue'
withDefaults(defineProps<{
    icon: string
}>(), {
})
const hoverColor = ref(false)
</script>

<style scoped lang="scss">

</style>