<template>
    <div class="font-['bafont'] text-[var(--main-white)]">
        <p class="text-[1.3rem] mb-[0.4rem] font-['bafontxi']  
                 lg:text-[3rem] lg:mb-[0.7rem]/">{{ welcomeTitle }}</p>
        <h1 class="relative 
            title-underline
            lg:after:top-[3.4rem] lg:after:right-[3.2rem] lg:after:h-[0.7rem]
            xxl:after:top-[4.3rem] xxl:after:right-[3.5rem] xxl:after:h-[0.7rem]
             ">
            <span class="text-[1.8rem] z-[1] relative
                         lg:text-[4rem] 
                         xxl:text-[5rem]
                         ">{{ mainTitle }}</span>
        </h1>
        <p class="w-full flex justify-end">
            <i class="mr-[0.45rem] 
                    skew-f
                    lg:before:w-[0.813rem] 
                    lg:before:h-[1rem] 
                    lg:after:w-[0.813rem] 
                    lg:after:h-[1rem] 
                    "></i>
            <i class="mr-[0.7rem]
                    skew-s
                    lg:before:w-[0.813rem] 
                    lg:before:h-[1rem] 
                    lg:after:w-[0.813rem] 
                    lg:after:h-[1rem] 
            "></i>
        </p>
    </div>
</template>

<script setup lang='ts'>
defineProps<{
    welcomeTitle: string , 
    mainTitle: string
}>()
</script>

<style lang="scss" scoped>

</style>