<template>
  <div class="outer-border w-full flex-col flex relative
              text-[1rem]">
    <div class="inner-border w-full transition-all duration-[var(--duration-time)]
                rounded-bl-[16px] rounded-tr-[16px] 
                text-[var(--main-white)] 
                hover:bg-[rgba(255,255,255,0.6)] 
                hover:text-[black]
                  hover:backdrop-blur-lg
                  p-[1rem]">
      <template v-for="(item, i) in content" :key="i">
        <span class="w-full" :class="classComputed(i)" :style="getStyle(item , i)">
          {{ item.text }}
        </span>
      </template>
    </div>
  </div>
</template>

<script setup lang='ts'>
import { withDefaults } from 'vue';
interface props {
    text:string,
    direction?:string,
    color?:string
}
const Props = withDefaults(defineProps<{
  content:props[]
}>(), {})


/*————————————————以下均为css配置——————————————*/
const classComputed = (i:number)=>{
  let classList: string[] = [];
  if (i !== Props.content.length - 1) {
    classList.push("mb-[0.5rem]");
  }
  if (i !== 0) {
    classList.push("[clip-path:inset(0_100%_0_0)]");
  }
  return classList.join(" ");
}
let animDuration: number = 0;
let animDelay: number = 0;
const getAnimationDuration = (textLength: number): number => {
  return Math.max(0.06 * textLength, 1);    //保证最少有1秒是持续时间
};
const getStyle = (item:props , i: number) => {
  const textLength = Props.content[i].text.length;
  const duration = getAnimationDuration(textLength);
  animDelay += animDuration;
  animDuration = duration;
  return `
    --animation-duration: ${duration}s;
    --animation-delay: ${animDelay}s;
    text-align: ${item.direction || ''};
    color: ${item.color || ''}; 
  `;
};
/*——————————————————————————————*/
</script>

<style scoped lang="scss">

@keyframes revealText {
  0% {
    clip-path: inset(0 100% 0 0);
  }
  100% {
    clip-path: inset(0 0 0 0);
  }
}

span {
  animation: revealText 
             linear 
             var(--animation-duration) 
             var(--animation-delay) 
             forwards;
  display: inline-block;
}
</style>