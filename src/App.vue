<script setup lang="ts">
import { onBeforeUnmount, onMounted, ref } from 'vue';
import MouseFollower from './components/sharedComponents/MouseFollower.vue';
import NavBar from './components/NavBar/NavBar.vue';

// console.log(import.meta.env.BASE_URL);
</script>

<template>
  <div class="container">
    <NavBar />

    <RouterView />
  </div>
  <MouseFollower />

</template>

<style lang="scss" scoped>
.container {
  overflow: hidden;
  width: 100%;
}
</style>