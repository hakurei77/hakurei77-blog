<template>
  <nav class="flex items-center relative h-full font-[bafont] text-base">
    <ul class="flex items-center">
      <li class="w-16 cursor-pointer flex mr-6 items-center relative 
                hover:text-[var(--main-color)] transition-colors duration-300"
        v-for="(item, i) in navList"
        :key="i"
        @mouseover="moveTriangle(i)"
        @mouseleave="moveTriangle(0)"
        @click="goRoute(item.path)">
        <SvgIconG v-if="item.icon != null" :name="item.icon" class="mr-3 mb-[1.2px] w-[1em] h-[1em]" />
        {{ item.title }}
      </li>
    </ul>
    <div
      :style="triangleStyle"
      class="triangle absolute top-0 transition-transform duration-300 bg-[var(--main-color)]"
    ></div>
  </nav>
</template>

<script setup lang='ts'>
import { withDefaults , ref , computed , onMounted } from 'vue'
import { useRouter } from "vue-router"

withDefaults(defineProps<{
  navList: { title: string; path: string; icon?:string}[],
}>(), {

})

const router = useRouter()
const goRoute = (dp: string) => {
  router.push(dp)
}

const trianglePosition = ref(0)
const moveTriangle = (index: number = 1) => {
  const liElements = document.querySelectorAll('li');
  const targetLi = liElements[index];
  const targetLiRect = targetLi.getBoundingClientRect();
  const navRect = liElements[0].parentElement?.getBoundingClientRect();
  if (navRect) {
    const offset = targetLiRect.left - navRect.left + targetLiRect.width / 2 + 4.5; // Adjust for triangle width
    trianglePosition.value = offset;
  }
}
const triangleStyle = computed(() => {
  return {
    transform: `translateX(${trianglePosition.value}px)`,
  };
})

onMounted(() => {
  moveTriangle(0)
})
</script>

<style scoped lang="scss">
.triangle {
  width: 15px; // Adjust based on your design
  height: 10px; // Adjust based on your design
  clip-path: polygon(50% 100%, 0% 0%, 100% 0%);
}
</style>