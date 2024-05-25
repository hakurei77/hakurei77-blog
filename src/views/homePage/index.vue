<template>
    <div class="relative">
        <Header class="absolute" />
        <div class="w-full h-[100vh] overflow-hidden">
            <img
            class="w-full h-full object-cover object-center"
            :src="HomepageImg"
            alt="背景图"
            />
        </div>
    </div>
</template>

<script setup lang='ts'>
import Header from '@/layout/Header/index.vue'
import HomepageImg from "@/assets/images/homepage.jpg"
</script>

<style scoped lang="scss">

</style>