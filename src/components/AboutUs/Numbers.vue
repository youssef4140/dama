<script setup lang="ts">


import { reactive } from 'vue';

const numbers = reactive([
    {
        title: '+20',
        desc: `We have successfully 
completed a total of
<b style="color:#4541F0;">20+ projects</b>`,
        video: '/images/about/wave.mp4'
    },
    {
        title: '$70k+',
        desc: `Average <b style="color:#4541F0;">annual sales</b> of managed accounts`,
        video: '/images/about/sphere.mp4'
    },
    {
        title: '+5',
        desc: `<b style="color:#4541F0;">Years</b> of accumulative experience withen marketing and business development`,
        video: '/images/about/clock.mp4'
    },
    {
        title: '+12',
        desc: `Our Team members bring <b style="color:#4541F0;">top-notch expertise</b>`,
        video: '/images/about/Cube.mp4'
    }

])



</script>

<template>
    <div class="numbers-container">
        <p class="sectionHeader">
            Our Story In Numbers
        </p>
        <div class="numbers-wrapper">
            <div v-for="num in numbers" :key="num.title" class="number">
                <p class="number-title" v-html="num.title"></p>
                <p class="number-desc" v-html="num.desc"></p>
                <!-- <div class="video"> -->
                <video autoplay muted loop>
                    <source :src="num.video" type="video/mp4">
                    Your browser does not support the video tag.
                </video>
                <!-- </div> -->
            </div>
        </div>
    </div>


</template>

<style lang="scss" scoped>
.numbers-container {
    margin-top: 2rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;

    .sectionHeader {
        font-size: 1rem;
        font-weight: 600;
        color: $grey;
        margin-left: 1rem;
    }

    // justify-content: space-between;
    .numbers-wrapper {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 11px;

        @media screen and (max-width: 768px) {
            grid-template-columns: 1fr;
            grid-template-rows: 1fr 1fr 1fr 1fr;

        }

        .number {
            // background-color: red;
            border-radius: $radius;
            padding: 1rem 1rem 4rem 1rem;
            // border: 2px solid black;
            display: flex;
            flex-direction: column;
            gap: 1rem;
            position: relative;
            overflow: hidden;
            background-color: lighten($offwhite, 3%);

            .number-title {
                font-size: 3rem;
                font-weight: 600;
            }

            .number-desc {
                font-size: 0.8rem;
                z-index: 1;
                width: 70%;


                @media screen and (max-width: 768px) {
                font-size: 1rem;

                    width: 50%;
                }
            }

            video {
                position: absolute;
                width: 70%;
                aspect-ratio: 1/1;
                bottom: -3rem;
                right: -3rem;
            }
        }

    }

    // background-color: red;
    // height:100%;
}
</style>