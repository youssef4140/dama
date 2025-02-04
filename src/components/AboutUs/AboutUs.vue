<script setup lang="ts">
import { reactive } from 'vue';
import Numbers from './Numbers.vue';
import Circle from './Circle/Circle.vue';
import SvgCircle from './Circle/SvgCircle.vue';



</script>

<template>
    <div class="section-container">

        <h1 class="sectionHeader">
            01- About Us
        </h1>
        <p class="sectionText bigger brd-btm">
            Redefining Traditional Marketing Approach </p>

      


        <div class="aboutUs-container">

            <div class="left">
                <p class="sectionText small ">
            In a crowded market filled with buzzwords like <span class="blue">data-driven</span> and <span
                class="blue">AI-integrated</span>, we stand out by focusing on what truly matters: clarity,
            simplicity, and <strong class="blue">results.</strong> </p>
                <div class="numbers-container">
                    <Numbers />
                </div>
            </div>
            <div class="right">
                <Circle />
            </div>

        </div>
    </div>
</template>

<style lang="scss" scoped>
.section-container {
    @include sectionPadding;
    padding-bottom:3rem;
    display: flex;
    flex-direction: column;
    gap: 2rem;

    p {
        color: black;

        @media screen and (min-width: 768px) {}
    }

    .brd-btm {
        border-bottom: 1px solid $darkblue;
        padding-bottom: 1rem;
    }

    .sectionText.small {
        @media screen and (min-width: 768px) {
            // width: 60%;
        }
    }

    .aboutUs-container {
        // display:flex;
        // flex-wrap: wrap;

        // @media screen and (min-width: 768px) {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 10rem;

        @media screen and (max-width: 768px) {
            grid-template-columns: 1fr;
            gap: 4rem;
            
        }
        // }


        .left,
        .right {
            // background-color: yellow;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }



        // .right{
        //     width:50vw;
        // }



    }
}
</style>