<template>
    <div class="flex justify-center items-center">
        <template v-for="(item, i) in navList" :key="i">
            <FuncButton :icon="item.title" class="hidden lg:flex" />
        </template>
        <Avatar class="ml-[4px]" :avatar="avatar" />
    </div>
</template>

<script setup lang='ts'>
import FuncButton from "@/components/Header/FuncButton/index.vue"
import Avatar from "@/components/Header/Avatar/index.vue"
import { withDefaults } from "vue";
withDefaults(defineProps<{
    navList:{
        title:string
    }[], 
    avatar: string 
}>(), {})
</script>

<style scoped lang="scss">

</style>