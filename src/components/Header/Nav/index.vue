<template>
  <nav class="flex items-center relative h-full">
    <ul class="hidden h-full items-center
                sm:flex">
      <li class="h-full cursor-pointer flex items-center
                mr-[24px] relative transition-all 
                hover:text-[var(--main-color)] duration-[var(--duration-time)]"
        v-for="(item, i) in navList"
        :key="i"
        @mouseover="moveTriangle(i)"
        @mouseleave="moveTriangle(0)"
        @click="goRoute(item.path)">
        <SvgIconG v-if="item.icon != null" :name="item.icon" class="mr-[8px] w-[1em] h-[1em]" />
        {{ item.title }}
      </li>
    </ul>
    <div
      :style="triangleStyle"
      class="[display:none] sm:flex triangle absolute top-0 
              transition-transform duration-[var(--duration-time)] bg-[var(--main-color)]"
    ></div>
  </nav>
</template>

<script setup lang='ts'>
import { withDefaults , ref , computed , onMounted } from 'vue'
import { useRouter } from "vue-router"

withDefaults(defineProps<{
  navList: { 
    title: string; 
    path: string; 
    icon?:string
  }[],
}>(), {})

const router = useRouter()
const goRoute = (dp: string) => {
  router.push(dp)
}
/*————————————————style————————————————————————————————*/
const trianglePosition = ref(0)
const moveTriangle = (index: number = 1) => {
  const liElements = document.querySelectorAll('li');
  const targetLi = liElements[index];
  const targetLiRect = targetLi.getBoundingClientRect();
  const navRect = liElements[0].parentElement?.getBoundingClientRect();
  if (navRect) {
    const offset = targetLiRect.left - navRect.left + targetLiRect.width / 2 + 5; 
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
/*————————————————style————————————————————————————————*/
</script>

<style scoped lang="scss">
.triangle {
  width: 15px;
  height: 10px;
  clip-path: polygon(50% 100%, 0% 0%, 100% 0%);
}
</style>