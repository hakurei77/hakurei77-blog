<template>
    <div class="w-[44px] h-[44px] cursor-pointer overflow-hidden 
                rounded-full transition-all duration-[var(--duration-time)]
                hover:scale-110 hover:shadow-lg">
        <img :src="avatar" alt="userAvatar">  
    </div>
</template>

<script setup lang='ts'>
import { withDefaults } from "vue";
withDefaults(defineProps<{ 
  avatar: string 
}>(), {});
</script>

<style scoped lang="scss">

</style>