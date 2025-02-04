<script setup lang="ts">
import NavBtns from './NavBtns.vue';
import NavMenu from './NavMenu.vue';


import { ref } from 'vue';
const isActive = ref(false);
const toggleMenu = () => {
    isActive.value = !isActive.value;
}
</script>

<template>
    <nav class="nav">
        <NavBtns @toggleMenu="toggleMenu()" />

    </nav>
        <NavMenu :isActive="isActive" />
</template>

<style lang="scss" scoped>
.nav{
    // background-color: red;
    display:flex;
    // margin-left:auto;
    top:3rem;
    right:1.6rem;
    padding:0 1.6rem;
    position: fixed;
    // height:4rem;
    // width:100%;
    z-index:3;
    @media screen and (max-width: 768px) {
        right:-1rem;
        
    }
}
</style>