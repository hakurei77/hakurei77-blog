<template>
    <svg :style="{ width , height , color }">
        <use :xlink:href="prefix + name" :fill="color"></use>
    </svg>
</template>

<script setup lang='ts'>
import { withDefaults } from 'vue';
withDefaults(defineProps<{
    name: string,
    width?: string,
    height?: string,
    color?: string,
    prefix?: string
}>(), {
    prefix: '#icon-'
})
</script>

<style scoped lang="scss">

</style>