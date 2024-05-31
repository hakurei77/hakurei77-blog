<template>
    <div class="text-[var(--main-white)]">
        <p class="text-[1.3rem] mb-[0.4rem] font-['bafontxi']  
                  sm:text-[1.5rem] sm:mb-[0.7rem]
                  xl:text-[1.6rem] xl:mb-[0.7rem]
                  ">
            {{ welcomeTitle }}
        </p>
        <h1 class="relative title-underline
            sm:after:top-[1.9rem] sm:after:right-[0.5rem]
            xl:after:top-[2.7rem] xl:after:right-[4.5rem] xl:after:h-[0.5rem]
             ">
            <span class="text-[1.8rem] z-[1] relative
                         sm:text-[2.3rem] 
                         xl:text-[3.2rem]
                         ">
                {{ mainTitle }}
            </span>
        </h1>
        <p class="w-full flex mt-[5px] justify-end">
            <i class="mr-[0.4rem] skew-f
                    xl:before:w-[0.7rem] 
                    xl:before:h-[0.81rem] 
                    xl:after:w-[0.7rem] 
                    xl:after:h-[0.8rem] 
                    "></i>
            <i class="mr-[1.8rem] skew-s
                    xl:before:w-[0.7rem] 
                    xl:before:h-[0.81rem] 
                    xl:after:w-[0.7rem] 
                    xl:after:h-[0.8rem] 
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