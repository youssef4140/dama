<template>
    <div class="mouse-follower" :style="dotStyle" :class="isMouseInWindow ? '' : 'inactive'"></div>
</template>

<script lang="ts" setup>
import { ref, computed, onMounted, onBeforeUnmount } from 'vue';




const isMouseInWindow = ref(true);
const mouseX = ref(0);
const mouseY = ref(0);
const dotX = ref(0);
const dotY = ref(0);

const dotStyle = computed(() => ({
    left: `${dotX.value}px`,
    top: `${dotY.value}px`,
}));

const handleMouseMove = (event: MouseEvent) => {
    mouseX.value = event.clientX;
    mouseY.value = event.clientY;
};

const animateDot = () => {
    const delay = 0.1; // 10% of the distance between the dot and the mouse
    dotX.value += Math.round((mouseX.value - dotX.value) * delay);
    dotY.value += Math.round((mouseY.value - dotY.value) * delay);
    requestAnimationFrame(animateDot);
};


const handlemouseover = () => {
    isMouseInWindow.value = true;
};

const handlemouseout = () => {
    isMouseInWindow.value = false;
};

onMounted(() => {
    window.addEventListener('mousemove', handleMouseMove);
    window.addEventListener('mouseover', handlemouseover);
    window.addEventListener('mouseout', handlemouseout);
    animateDot();
});

onBeforeUnmount(() => {
    window.removeEventListener('mousemove', handleMouseMove);
    window.removeEventListener('mouseover', handlemouseover);
    window.removeEventListener('mouseout', handlemouseout);
});




</script>

<style lang="scss" scoped>
.mouse-follower {
    position: fixed;
    width: 10px;
    height: 10px;
    background-color: $darkblue;
    border-radius: 50%;
    pointer-events: none;
    transition: transform 0.5s ease-in-out, opacity 0.5s ease-in-out;

    z-index: 9999;

    @media screen and (max-width: 768px) {
        display: none;
        
    }

    &.inactive {
        transform: scale(0);
        opacity: 0;
    transition: transform 0.5s ease-in-out, opacity 0.5s ease-in-out;


    }
}
</style>
