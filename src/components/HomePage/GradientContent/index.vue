<template>
  <div class="out w-full font-[cursive]
              text-[1rem] 
              lg:text-[1.2rem]
              xxl:text-[1.3rem] 
              flex-col flex relative ">
    <div class="in w-full p-[1rem] text-[var(--main-white)] 
                hover:bg-[rgba(255,255,255,0.6)] 
              transition-all duration-300 hover:text-[black]
              rounded-bl-[1rem] rounded-tr-[1rem] hover:backdrop-blur-lg">
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
.out:before {
    content: '';
    position: absolute;
    z-index: 1;
    top: 0;
    left: 0;
    height: 30px;
    width: 30px;
    background-color: var(--main-color);
    -webkit-clip-path: polygon(100% 0%,90% 10%,10% 10%,10% 90%,0% 100%,0% 0%);
            clip-path: polygon(100% 0%,90% 10%,10% 10%,10% 90%,0% 100%,0% 0%);
}
.out:after {
  content: '';
  position: absolute;
  z-index: 1;
  bottom: 0;
  right: 0;
  height: 30px;
  width: 30px;
  background-color: var(--main-color);
  -webkit-clip-path: polygon(90% 10%,100% 0%,100% 100%,0% 100%,10% 90%,90% 90%);
          clip-path: polygon(0% 100%,10% 90%,90% 90%,90% 10%,100% 0%,100% 100%);
  
}
.in:before{
  content: '';
  position: absolute;
  z-index: 1;
  top: 6px;
  left: 6px;
  height: 12px;
  width: 12px;
  background-color: var(--main-color);
  -webkit-clip-path: polygon(100% 0%,90% 15%,15% 15%,15% 90%,0% 100%,0% 0%);
          clip-path: polygon(100% 0%,90% 15%,15% 15%,15% 90%,0% 100%,0% 0%);
}
.in:after{
  content: '';
  position: absolute;
  z-index: 1;
  bottom: 6px;
  right: 6px;
  height: 12px;
  width: 12px;
  background-color: var(--main-color);
  -webkit-clip-path: polygon(80% 20%,100% 0%,100% 100%,0% 100%,20% 80%,80% 80%);
          clip-path: polygon(80% 20%,100% 0%,100% 100%,0% 100%,20% 80%,80% 80%);
}
</style>