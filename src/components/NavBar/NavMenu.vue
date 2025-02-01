<script setup lang="ts">
import { watch, type Ref } from 'vue';
import LeftMenu from './SmallerComps/leftMenu.vue';
import RightMenu from './SmallerComps/rightMenu.vue';

const props = defineProps<{
    isActive: boolean;
}>();

watch(() => props.isActive, (newVal) => {
    if (newVal) {
        document.body.style.overflow = 'hidden';
        
    } else {
        document.body.style.overflow = 'auto';
    }
});
</script>

<template>
    <div class="nav-menu-container" :class="{ active: isActive }">
        <div class="nav-left">
            <LeftMenu class="slct" />
        </div>
        <div class="nav-right">
            <RightMenu class="slct" />
        </div>
    </div>
</template>

<style lang="scss" scoped>
.nav-menu-container {
    height: 100vh;
    width: 100%;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 2;
    display: flex;
    pointer-events: none;


    .nav-left {
        transition: transform 0.8s ease-in-out;
        width: 20%;
        height: 100%;
        background-color: darken($darkblue, 10%);
        transform-origin: top;
        padding: 2.3rem;
        transform: scaleY(0);
    }

    .nav-right {
        transition: transform 0.8s ease-in-out;
        width: 80%;
        height: 100%;
        background-color: $darkblue;
        padding: 2.3rem;
        transform-origin: bottom;
        transform: scaleY(0);
    }

    .slct {
        transition: opacity .2s ease-in-out;
        opacity: 0;
    }

    &.active {
        pointer-events: all;

        .nav-left,
        .nav-right {
            transition: transform 0.8s ease-in-out;

            transform: scaleY(1);
        }

        .slct {
            transition: opacity 1s ease-in;

            opacity: 1;
        }
    }

    @media screen and (max-width: 768px) {
        .nav-right {
            width: 100%;
        }

        .nav-left {
            display: none;
        }

    }
}
</style>