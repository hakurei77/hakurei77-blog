<template>
    <div class="flex items-center">
        <div class="w-[16rem] ml-[32px]
                    sm:w-[20rem]
                    sm:ml-[64px] sm:absolute sm:top-[13rem]
                    xl:w-[34rem]
                   ">
            <Title class="w-[110%] font-['bafont']"
                    :welcome-title="title" 
                    :main-title="mainTitle" />
            <div class="w-full my-[10px]
                        sm:mt-[0.6rem] sm:mb-[0.6rem]">
                <img class="w-full" :src="StyleLine" alt="dividingLine"> 
            </div>
            <GradientContent class="w-full font-[cursive]" :content="content" />
           
        </div>
        <PosterArrow class="absolute bottom-[16px]" />
    </div>
</template>

<script setup lang='ts'>
import Title from "./Title/index.vue"
import GradientContent from "./GradientContent/index.vue"
import Author from "./Author/index.vue"
import PosterArrow from "./posterArrow/index.vue"
import StyleLine from "@/assets/images/styleline.png"
import AuthorImg from "@/assets/images/author.jpg"

let title = "欢迎来到"
let mainTitle = "博丽七七的博客小窝"
let content = [
    {
        text:"风带来故事的种子，时间使之发芽；"
    },
    {
        text:"终点并不意味着一切，在抵达终点之前，用你的眼睛多多观察这个世界吧。"
    },
    {
        text:"--温迪",
        direction:"right",
        color:"#01e0b0"
    }
]
let enName="hakurei77"
let cnName="博丽七七"
let introduction="大二，蓝桥杯省二，喜欢前端开发，特别是做网页，热爱开源，喜欢分享"
let linkList = [
    {
        icon:"github",
        color:"white"
    },
    {
        icon:"weixin",
        color:"#63ba38"
    },
    {
        icon:"qq",
        color:"#42aeec"
    },
    {
        icon:"email",
        color:"#f9d129"
    }

]
</script>

<style scoped lang="scss">

</style>