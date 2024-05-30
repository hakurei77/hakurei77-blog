<template>
    <div class="relative">
        <div class="w-full h-[100vh] overflow-hidden absolute z-[1]">
            <img class="w-full h-full object-cover object-center"
                :src="HomepageImg" alt="背景图"/>
        </div>
        <Header class="fixed z-[3]" />
        <HomePage class="w-full h-[100vh] absolute z-[2]" />
        <div class="w-full h-[200vh]">

        </div>
    </div>
</template>

<script setup lang='ts'>
import Header from '@/layout/Header/index.vue'
import HomepageImg from "@/assets/images/16.jpg"
import HomePage from "@/components/HomePage/index.vue"
</script>

<style scoped lang="scss">

</style>