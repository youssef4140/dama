<script setup lang="ts">
import HeroContent from './HeroContent.vue';
import HeroNav from './HeroNav.vue';

</script>

<template>
    <div class="hero">
        <div class="hero_hero">
        <HeroContent />

        </div>
        <HeroNav />

    

    </div>
</template>

<style lang="scss" scoped>
.hero{
    background-color: $offwhite;
    // background-color: red;
    min-height: 100vh;
    // border-radius: $radius;
    display:flex;
    flex-direction: column;
    // justify-content: center;
    align-items: center;
    padding-top:2vh;
}
.hero_hero {
    width:98%;
    min-height: 95vh;

    background-color: white;
    border-radius: $radius ;
    // background-color: yellow;
    display: flex;
    flex-direction: column;
    overflow: hidden;
    // @media screen and (max-width: 768px) {
        // width:96%;
        
    // }

}

</style>