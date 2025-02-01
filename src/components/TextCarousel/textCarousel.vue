<script setup lang="ts">
import InfiniteCarousel from '../sharedComponents/InfiniteCarousel.vue';

</script>



<template>
        <InfiniteCarousel :animationDuration="15" >
        <h1>Relevance</h1><h1> Results Driven</h1><h1> Simplicity</h1><h1> Trendy</h1>
    </InfiniteCarousel>
</template>


<style lang="scss" scoped>
    h1 {
            font-size: clamp(6rem, 10vw, 10rem);
            font-weight: 700;
            margin: 0;
            padding: 0 1rem;
            white-space: nowrap;
            color:$blue;
        }
</style>