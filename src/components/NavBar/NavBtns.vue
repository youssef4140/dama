<script setup lang="ts">
import { ref } from 'vue';
import ClientBtn from './SmallerComps/clientBtn.vue';
import MenuBtn from './SmallerComps/menuBtn.vue';
import MessageBtn from './SmallerComps/messageBtn.vue';
const emit = defineEmits(['toggleMenu']);

const isActive = ref(false);
const toggleMenu = (e: boolean) => {
    isActive.value = e;
    emit('toggleMenu', e);
}

</script>

<template>
    <div class="nav_btns_wrapper">
        <ClientBtn :isActive="isActive"/>
        <MessageBtn :isActive="isActive" />
        <MenuBtn @toggleMenu="toggleMenu($event)" :isActive="isActive" />

    </div>
</template>

<style lang="scss" scoped>
.nav_btns_wrapper {
    height:100%;
    // position: absolute;
    // right:1.6rem;
    // top:0;
    margin-left:auto;
    display:flex;
    align-items:center;
    justify-content: center;
    // justify-content: flex-end;
    gap:2rem;
    @media(max-width:375px){
        gap:0.5rem;
        
    }
    // padding:1rem;
}
</style>