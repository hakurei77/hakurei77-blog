<template>
    <div class="w-10 h-10 bg-white rounded-full 
                ml-2 mr-2 hover:scale-110 transition-all
                hover:shadow-lg
                cursor-pointer overflow-hidden">
        <img :src="Avatar" alt="">  
    </div>
</template>

<script setup lang='ts'>
import Avatar from "@/assets/images/avatar.png"
</script>

<style scoped lang="scss">

</style>