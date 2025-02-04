<script setup lang="ts">
import { onMounted, ref } from 'vue';
import InfiniteCarousel from '../sharedComponents/InfiniteCarousel.vue';

const images = ref<string[]>([]);
const importImages = import.meta.glob('@/assets/Clients/*.{jpg,png,gif}', { eager: true });

for (const path in importImages) {
  images.value.push((importImages[path] as { default: string }).default);
}

console.log(images.value);
</script>



<template><InfiniteCarousel>  <div  class="image-wrapper">
    <img v-for="image in images" :key="image" :src="image" alt="Client Image" class="image" />
  </div></InfiniteCarousel></template>

<style lang="scss" scoped>
.image-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    gap:5rem;
    border-top: 1px solid lighten($grey, 20%);
    padding-top:2rem;
    // padding: 1rem;
    // border:1px solid rgba(157, 157, 157,0.4);
    // margin-right:1rem;

    .image {
        width: 11rem;
        // aspect-ratio: 1/1;
    }
 
}
</style>