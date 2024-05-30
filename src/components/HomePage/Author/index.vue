<template>
    <div class="w-full h-[12rem] flex items-center mt-[1rem] relative">
        <div class="absolute right-0 w-[85%] bg-green-500 h-full flex items-center">
            <div class="absolute w-[10rem] h-[10rem] rounded-full overflow-hidden ml-[-5rem]">
                <img class="w-full h-full rounded-full" :src="authImg" alt="作者头像">
            </div>
            <div class="absolute right-0 top-[1rem] w-[80%] bg-red-500 flex flex-col font-[cursive]">
                <span class="gradient-text mb-[0.5rem]">{{ enName }}</span>
                <span class="text-[2rem] mb-[0.5rem] font-[600]">{{ cnName }}</span>
                <span class="pr-[1rem] leading-tight">{{ introduction }}</span>
            </div>
            <div class="absolute bottom-[0.6rem] right-0 w-[80%] flex">
                <template v-for="item,i in linkList" :key="i">
                    <div class="linkSvg w-[2rem] h-[2rem] rounded-full mr-[1rem] 
                                flex items-center justify-center cursor-pointer active:[opacity:0.8] hover:bg-[item.color]
                                " :style="{ 
                                    border:`1px solid ${item.color}`,
                                    }">
                        <SvgIconG :name="item.icon" class="w-[80%] h-[80%]" />
                    </div>
                </template>
                
            </div>
        </div>
    </div>
</template>

<script setup lang='ts'>
import { withDefaults , onMounted } from 'vue';
withDefaults(defineProps<{ 
    authImg: string, 
    enName:string,
    cnName:string,
    introduction:string,
    linkList: {
        icon: string,
        color: string
    }[]
}>(), {})

onMounted(()=>{
    
})

</script>

<style scoped lang="scss">
 @keyframes colorGradient {
    0% {
        background-position: 0% 50%;
    }
    50% {
        background-position: 100% 50%;
    }
    100% {
        background-position: 0% 50%;
    }
}
.gradient-text {
    background: linear-gradient(to right, #ff6b6b, #ffa500, #ffff00, #00ff00, #00ffff, #0000ff, #8b00ff);
    background-size: 200% 200%;
    animation: colorGradient 10s ease infinite;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}
</style>