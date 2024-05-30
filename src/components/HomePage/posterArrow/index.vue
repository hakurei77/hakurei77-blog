<template>
    <div class="w-full flex flex-col items-center cursor-pointer">
        <img :src="PosterArrow" alt="posterarrow" class="arrow arrow-1" />
        <img :src="PosterArrow" alt="posterarrow" class="arrow arrow-2" />
        <img :src="PosterArrow" alt="posterarrow" class="arrow arrow-3" />
    </div>
</template>

<script setup lang='ts'>
import PosterArrow from "@/assets/icons/posterarrow.png";
</script>

<style scoped lang="scss">
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
</style>