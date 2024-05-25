<template>
    <div class="w-8 h-8 rounded-full cursor-pointer 
                hover:shadow-md hover:bg-[--main-color] 
                transition-all duration-200
                flex items-center justify-center
                ml-1 mr-1
                "
     @mouseover="hoverColor = true" 
     @mouseleave="hoverColor = false">
  <SvgIconG :name="icon" :color="hoverColor ? '#fff' : ''" class="w-[80%] h-[80%] transition-all duration-200"></SvgIconG>
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