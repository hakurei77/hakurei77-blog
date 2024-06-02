<template>
    <header class="w-full h-[var(--header-height)] px-[24px] font-[bafont] text-[18px]
                    bg-[rgba(255,255,255,0.7)] backdrop-blur-lg 
                    text-[--header-text-color] [border-bottom:2px_solid_var(--main-color)]
                    xl:[border-bottom:2px_solid_transparent]
                    ">
        <div class="headerLine
                        hidden xl:block opacity-0 w-full h-[var(--header-height)] absolute top-0 right-0 
                        [transform-origin:center_bottom] [transform:scaleX(0.002)]
                        [border-bottom:2px_solid_var(--main-color)]"></div>
        <div class="headerArrow
                        hidden xl:block 
                        opacity-0 w-[36px] h-[var(--header-height)] 
                        absolute top-0 left-[50%] [transform:translateX(-50%)]"></div>
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
import { onMounted , ref , withDefaults } from "vue"

const props = withDefaults(defineProps<{
    scroller: string
    trigger:string
}>(),{})

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

const rightArrow = ref("polygon(50% 20%, 50% 0, 0% 50%, 50% 100%, 50% 80%, 20% 50%)");
const leftArrow = ref("polygon(50% 20%, 50% 0, 100% 50%, 50% 100%, 50% 80%, 80% 50%)");
const direction = ref("down")

import gsap from "gsap"
import { ScrollTrigger } from "gsap/ScrollTrigger";
onMounted(()=>{
    gsap.registerPlugin(ScrollTrigger);
    gsap.to('header', { backgroundColor: 'rgba(255,255,255,0)', backdropFilter: 'blur(0px)',
        scrollTrigger: { scroller:`.${props.scroller}`, trigger: `.${props.trigger}`, start: 'top top', end: 'top -100%', scrub: true }});
    gsap.to(".headerLine", { scaleX:1, opacity:1,
        scrollTrigger: { scroller:`.${props.scroller}`, trigger: `.${props.trigger}`, start: "top top", end: "top -100%", scrub: true,}})
    gsap.to(".headerArrow" , { width:"102%",
        scrollTrigger: { scroller:`.${props.scroller}`, trigger: `.${props.trigger}`, start: "top top", end: "top -100%", scrub: true,}})
    gsap.to(".headerArrow" , { opacity:1,
        scrollTrigger: { scroller:`.${props.scroller}`, trigger: `.${props.trigger}`, start: "top top", end: "top -10%", scrub: true,}})

    let lastScrollTop = 0;
    const target =  document.querySelector(`.${props.scroller}`) as HTMLElement
    const handleScroll = () => {
        const scrollTop = target.scrollTop || document.documentElement.scrollTop;
        let nowDirection = '';
        scrollTop > lastScrollTop ? nowDirection = "down" : nowDirection = "up";
        if (nowDirection !== direction.value) {
            direction.value = nowDirection;
            [rightArrow.value, leftArrow.value] = [leftArrow.value, rightArrow.value];
        }
        lastScrollTop = scrollTop <= 0 ? 0 : scrollTop; // For Mobile or negative scrolling
    };
    target.addEventListener("scroll", handleScroll);
})

</script>

<style scoped lang="scss">
.headerArrow::before{
    clip-path:v-bind('rightArrow');
}
.headerArrow::after {
    clip-path:v-bind('leftArrow');
}
</style>