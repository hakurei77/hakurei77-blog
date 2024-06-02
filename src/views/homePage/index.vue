<template>
  <div class="w-full h-[100vh] overflow-hidden fixed z-[-1]">
    <img class="w-full h-full object-cover object-center" :src="HomepageImg" alt="背景图" />
  </div>
  <Header class="fixed z-[1]" scroller="contentPage" trigger="contentPage" />
  <HomePage class="w-full h-[100vh] fixed" />
  <div class="contentPage 
                w-full h-[100vh] [scroll-snap-type:y_proximity] absolute overflow-auto">
    <div class="posterArrow 
                  w-full h-[100vh] [scroll-snap-align:start]">
      <PosterArrow class="absolute bottom-[32px]" :up="up" @click="showContentPage" />
    </div>
    <div class="w-full bg-white [scroll-snap-align:start]" :style="{
      'scroll-snap-align': scrollSnapAlign
    }">
      <div class="w-[500px] h-[300px] mb-4 bg-red-400">Ss</div>
      <div class="w-[500px] h-[300px] mb-4 bg-red-400">afaf</div>
      <div class="w-[500px] h-[300px] mb-4 bg-red-400">faf</div>
      <div class="w-[500px] h-[300px] mb-4 bg-red-400">afa</div>
      <div class="w-[500px] h-[300px] mb-4 bg-red-400">afa</div>
      <div class="w-[500px] h-[300px] mb-4 bg-red-400">33</div>
    </div>
  </div>

</template>

<script setup lang='ts'>
import { ref, onMounted, watchEffect } from 'vue';
import Header from '@/layout/Header/index.vue'
import HomePage from "@/components/HomePage/index.vue"
import PosterArrow from "@/components/ContentPage/PosterArrow/index.vue"

import HomepageImg from "@/assets/images/16.jpg"

let up = ref(false);
let scrollSnapAlign = ref("start")
let nowScroll = 0;
let lock = true;

onMounted(() => {
  watchEffect(() => {
    window.addEventListener("wheel", (e) => { nowScroll = e.deltaY })
    document.querySelector(".contentPage")?.addEventListener("scroll", (e) => {
      const event = e.target as HTMLElement
      if (lock === true && nowScroll > 0) { scrollSnapAlign.value = "start"; lock = false }
      if (event.scrollTop >= window.innerHeight) scrollSnapAlign.value = "none"
      if (event.scrollTop < window.innerHeight) lock = true
      if (event.scrollTop === 0) scrollSnapAlign.value = "start"
      if (event.scrollTop === 0 || event.scrollTop >= window.innerHeight) up.value = false
      if (event.scrollTop !== 0 && event.scrollTop < window.innerHeight) up.value = true
    })
  })
});

const showContentPage = () => {
  document.querySelector(".contentPage")?.scrollTo({
    top: window.innerHeight,
    behavior: 'smooth',
  });
};

</script>

<style scoped lang='scss'></style>