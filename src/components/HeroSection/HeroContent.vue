<script setup lang="ts">
import { onMounted, ref } from 'vue';
import BtnDown from '../sharedComponents/BtnDown.vue';
import HeroList from './HeroList.vue';

const businesses = ref('B');
const cursorIsdisplayed = ref(true);

const sleep = (ms:number) => {
    return new Promise(resolve => setTimeout(resolve, ms));
};

const constructText = async (text:String) => {
    businesses.value = 'B';
    cursorIsdisplayed.value = true;
    for (let i = 0; i < text.length; i++) {
        await sleep(150);

            businesses.value += text[i];
    }
    await sleep(1500);
    
    cursorIsdisplayed.value = false;
};

onMounted(() => {
    constructText('USINESSES');

});
</script>

<template>

    <div class="hero-wrapper">
        <div class="video">
            <video autoplay muted loop>
                <source src="/images/animation.mp4" type="video/mp4">
                Your browser does not support the video tag.
            </video>
        </div>
        <div class="mid-line responsive">
            <BtnDown :height="'7rem'" :width="'7rem'" />
            <div class="line-wrapper">
                <div class="text">
                    <span>Scroll</span>

                </div>
                <div class="line"></div>
                <div class="text">
                    <span>Down</span>

                </div>
            </div>
        </div>
        <div class="slogan-wrapper">
            <h1 class="fst">IN THE BUSINESS</h1>
            <div class="btn-wrapper">
                <BtnDown class="btn-pc" />
                <h1 class="snd">OF <span class="bold">GROWING</span></h1>

            </div>
            <h1 class="trd cursor" :class="cursorIsdisplayed?'':'inactive'">{{ businesses }}</h1>
        </div>
        <div class="list-wrapper">
            <HeroList />
        </div>
    </div>
</template>

<style lang="scss" scoped>
$hero-font: 6rem;

@mixin hero-font($size) {
    font-size: $size;

    @media screen and (max-width: 768px) {
        font-size: $size * 0.9;

    }

    @media screen and (max-width: 576px) {
        font-size: $size * 0.6;

    }
    @media screen and (max-width: 410px) {
        font-size: $size * 0.5;

    }
    @media screen and (max-width: 320px) {
        font-size: $size * 0.4;

    }
    
}

.hero-wrapper {
    flex-grow: 1;
    display: flex;
    justify-content: space-between;
    position: relative;
    padding: 2rem;

    @media screen and (max-width: 768px) {
        flex-direction: column-reverse;
        // align-items: center;
        // justify-content: flex-start;
        padding: 4rem 1rem;

    }

    .video {
        position: absolute;
        right: 0%;
        bottom:1px;

        // z-index: -1;
        @media screen and (max-width: 768px) {
            position: static;
            align-self: center;


        }

        video {
            height: 40rem;
            // width: 40rem;
            object-fit: cover;

            @media screen and (max-width: 768px) {
                height: 30rem;
                // width: 25rem;

            }
        }

        // height:60px;
        // width: 100%;
        // z-index: -1;
    }

    .slogan-wrapper {
        display: flex;
        flex-direction: column;
        justify-content: center;
        user-select: none;

        z-index: 1;

        .fst {
            font-weight: 400;
        }

        .btn-wrapper {
            display: flex;
            align-items: center;

            .btn-pc {
                @media screen and (max-width: 768px) {
                    pointer-events: none;
                    visibility: hidden;
                }

            }

            .snd {
                font-weight: 400;

                .bold {
                    font-weight: 700;
                }
            }
        }

        .trd {
            @include hero-font($hero-font * 1.33);

            @media screen and (max-width: 768px) {
                @include hero-font($hero-font);

            }

        }
    }

    .list-wrapper {
        display: flex;
        justify-content: flex-end;
        align-items: center;
        z-index: 1;

        @media screen and (max-width: 768px) {
            display: none;

        }
    }

    .mid-line {
        width: 100vw;

        @media screen and (max-width: 768px) {
            display: flex;
            align-items: center;
        }

        .line {
            height: 1px;
            width: 70vw;
            background-color: $black;
        }
    }
}

h1 {
    @include hero-font($hero-font);
    font-weight: 700;
    color: $black;
    margin: 0;
}



.trd {
    animation: animate 4s ease infinite;
    // text-shadow: -4px 2px 0 hotpink, 4px -2px 0 blue;

    text-shadow: 0.2rem 0.15rem 0 hotpink, -0.2rem -0.15rem 0 blue;
    position: relative;
    // @keyframes animate {
    //     0%{
    //         text-shadow: -0px 0px 0 hotpink, 0px -0px 0 blue;
    //     }

    //     25% {
    //         text-shadow: -3px 2px 0 hotpink, 3px -2px 0 blue;
    //     }

    //     50% {
    //         text-shadow: -0px 0px 0 hotpink, 0px -0px 0 blue;
    //     }

    //     75% {
    //         text-shadow: -3px 2px 0 hotpink, 3px -2px 0 blue;
    //     }
    //     100% {
    //         text-shadow: -0px 0px 0 hotpink, 0px -0px 0 blue;
    //     }
    // }
    // border-right:2rem solid black;
    width: fit-content;
    animation: cursor .4s step-end infinite alternate;
    @keyframes cursor {
        50% {
            border-right-color: transparent;
        }

    }
    @media screen and (max-width: 768px) {
        text-shadow: 0.1rem 0.08rem 0 hotpink, -0.1rem -0.08rem 0 blue;
        letter-spacing: 0.1rem;
        
    }
 




}

.responsive {
    @media screen and (min-width: 768px) {
        display: none;

    }
}

.cursor{
    &::after {
        content: '';
        position: absolute;
        top: 0;
        width: 1.2rem;
        height: 100%;
        background-color: $black;
        right:-1.9rem;
        animation: blink 1s infinite;
        transition: opacity 0.5s ease-in-out;
        @keyframes blink {
            50% {
            background-color: transparent;

        }
        }

    }
    &.inactive::after{
        transition: opacity 0.5s ease-in-out;
        opacity: 0;
    }
}
</style>