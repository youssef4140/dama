<script setup lang="ts">
const props = defineProps<{
    isActive: boolean;
}>();
const emit = defineEmits(['toggleMenu']);

</script>

<template>
    <div class="btn-wrapper" :class="{ 'active': props.isActive }">
        <svg width="27" height="26" viewBox="0 0 27 26" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M20.3112 20.9401H22.6093C24.2012 20.9401 25.4941 19.6512 25.4941 18.0581V3.88142V3.88087C25.4932 2.28792 24.2003 1 22.6088 1H3.88476C2.2929 1 1 2.2889 1 3.882V18.0581C1 19.6512 2.2929 20.9401 3.88476 20.9401H13.266L17.3553 24.4553C17.3554 24.4554 17.3555 24.4555 17.3557 24.4556C18.5129 25.4508 20.3112 24.6319 20.3112 23.1003V20.9401Z" fill="#E3E7FC" stroke-width="2"/>
</svg>



    </div>
</template>

<style lang="scss" scoped>
.btn-wrapper {
    padding: 1.8rem;
    height: 100%;
    background-color: white;
    border: 1px solid $darkblue;
    border-radius: 100vh;
    position: relative;
    cursor: pointer;
    transition: all 0.8s;

    display: flex;
    align-items: center;
    justify-content: center;

    >svg{
        position: absolute;
        top:50%;
        left:50%;
        transform: translate(-50%, -50%);
        height:48%;
        width:48%;
        
        >path {
        fill: $darkblue;
    }}

    &.active {
        background-color: white;
        
    }


}
</style>