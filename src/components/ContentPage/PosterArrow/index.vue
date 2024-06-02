<template>
    <div class="w-full flex flex-col items-center">
        <div class="cursor-pointer transition-all duration-[var(--duration-time)]"
            @mouseenter="mouseEnter(up)"
            @mouseleave="mouseLeave(up)"
            :class="{ 
                'arrowRotateOne': hoverAnimationOne,
                'arrowRotateTwo': hoverAnimationTwo
            }">
            <img :src="PosterArrow" alt="posterarrow" class="arrow arrow-1" />
            <img :src="PosterArrow" alt="posterarrow" class="arrow arrow-2" />
            <img :src="PosterArrow" alt="posterarrow" class="arrow arrow-3" /> 
        </div>
    </div>
</template>

<script setup lang='ts'>
import { ref,withDefaults,watchEffect } from 'vue';
import PosterArrow from "@/assets/icons/posterarrow.png";
const props = withDefaults(defineProps<{
    up?:boolean
}>(),{
    up:false
})
const hoverAnimationOne = ref(false);
const hoverAnimationTwo = ref(false);

function mouseEnter(up:boolean){
    if(!up){
        hoverAnimationOne.value = true , hoverAnimationTwo.value = false
    }
}
function mouseLeave(up:boolean){
    if(!up){
        hoverAnimationOne.value = false , hoverAnimationTwo.value = true
    }
}

watchEffect(()=>{
    if(props.up){
        hoverAnimationOne.value = true , hoverAnimationTwo.value = false
    }
    if(!props.up){
        hoverAnimationOne.value = false , hoverAnimationTwo.value = true
    }
})

</script>

<style scoped lang="scss">
.arrowRotateOne{
    animation: arrowRotateOne 1s linear forwards;
}
.arrowRotateTwo{
    animation: arrowRotateTwo 1s linear forwards;
}
.arrow {
    animation: arrow 1.5s linear infinite;
    &-1 {
        animation-delay: 0s;
    }
    &-2 {
        animation-delay: 0.5s;
    }
    &-3 {
        animation-delay: 1s;
    }
}

@keyframes arrow {
    50% {
        opacity: 0;
    }
}
@keyframes arrowRotateOne {
    25%{
        opacity: 0;
        transform: rotate(0deg);
    }
    50%{
        opacity: 0;
        transform: rotate(180deg);
    }
    100% {
        opacity: 1;
        transform: rotate(180deg);
    }
}
@keyframes arrowRotateTwo {
    0%{
        opacity: 1;
        transform: rotate(180deg);
    }
    25%{
        opacity: 0;
        transform: rotate(180deg);
    }
    50%{
        opacity: 0;
        transform: rotate(0deg);
    }
    100% {
        opacity: 1;
        transform: rotate(0deg);
    }
}
</style>