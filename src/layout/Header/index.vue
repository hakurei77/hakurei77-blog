<template>
    <header class="w-full h-16 flex items-center 
                    bg-[rgba(255,255,255,0.7)] backdrop-blur-lg 
                    text-[--header-color] border-color">
        <img class="h-full ml-6 mr-6 cursor-pointer hover:opacity-70 transition-all duration-300" :src="hakurei77logo" alt="logo">
        <Nav :nav-list="NavList" class="flex-grow"/>
        <RightNav class="absolute right-0 mr-6"/>
    </header>
</template>

<script setup lang='ts'>
import hakurei77logo from "@/assets/images/hakurei77logo.png"
import Nav from "@/components/Header/Nav/index.vue"
import RightNav from "@/components/Header/RightNav/index.vue"

const NavList = [
    { title: "首页", path: "/" , icon:"homepage"},
    { title: "文章", path: "/opaofg" , icon:"article"},
    { title: "其他", path: "/opaofg" ,icon:"other"},
    { title: "设置", path: "/opaofg" ,icon:"setting"},
    { title: "关于", path: "/opaofg",icon:"about" },
    { title: "管理", path: "/opaofg" ,icon:"manage"}
]

</script>

<style scoped lang="scss">
.border-color{
    border-bottom: 1px solid var(--main-color);
}
</style>