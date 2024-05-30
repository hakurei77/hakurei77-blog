<template>
    <div>
        <div class="w-[16rem] ml-10 rounded-lg
                    lg:ml-20 
                    lg:w-[39rem]
                    xxl:w-[48rem] ">
            <Title class="w-[110%]"
                    :welcome-title="title" 
                    :main-title="mainTitle" />
            <div class="w-[110%] 
                        mt-[0.5rem] mb-[0.5rem]
                        lg:mt-[0.6rem] lg:mb-[0.6rem]
                        xxl:mt-[1rem] xxl:mb-[1rem]
                        ">
                <img class="w-full" :src="StyleLine" alt=""> 
            </div>
            <GradientContent :content="content" />
            <Author :authImg="AuthorImg"
                    :enName="enName"
                    :cnName="cnName"
                    :introduction="introduction"
                    :linkList="linkList"
            ></Author>
        </div>
    </div>
</template>

<script setup lang='ts'>
import Title from "./Title/index.vue"
import GradientContent from "./GradientContent/index.vue"
import Author from "./Author/index.vue"
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