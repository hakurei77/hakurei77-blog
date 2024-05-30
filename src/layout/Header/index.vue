<template>
    <header class="w-full h-[var(--header-height)] px-[24px] font-[bafont] text-[18px]
                    bg-[rgba(255,255,255,0.7)] backdrop-blur-lg 
                    text-[--header-text-color] [border-bottom:1px_solid_var(--main-color)]">
        <div class="w-full h-full relative flex items-center">
            <img class="h-full cursor-pointer transition-all duration-[var(--duration-time)]
                        hover:opacity-70" 
                        :src="hakurei77logo" alt="logo">
            <Nav :nav-list="NavList" class="mx-[24px]" />
            <RightNav class="absolute right-0 mx-[4px]" :avatar="avatar" :nav-list="RightNavList"/>
        </div>
    </header>
</template>

<script setup lang='ts'>
import Nav from "@/components/Header/Nav/index.vue"
import RightNav from "@/components/Header/RightNav/index.vue"
import hakurei77logo from "@/assets/images/hakurei77logo.png"
import avatar from "@/assets/images/avatar.png"
const NavList = [
    { title: "首页", path: "/" , icon:"homepage"},
    { title: "文章", path: "/opaofg" , icon:"article"},
    { title: "其他", path: "/opaofg" ,icon:"other"},
    { title: "设置", path: "/opaofg" ,icon:"setting"},
    { title: "关于", path: "/opaofg",icon:"about" },
    { title: "管理", path: "/opaofg" ,icon:"manage"},
]
const RightNavList = [
    { title: "search"},
    { title: "color"},
    { title: "pause"},
    { title: "sunset"},
]

</script>

<style scoped lang="scss">
</style>