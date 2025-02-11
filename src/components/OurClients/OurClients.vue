<script setup lang="ts">
import { ref, type Ref } from 'vue';
import Carousel from '../sharedComponents/Carousel.vue';


const clients = [
    {
        quote: 'I wouldn’t launch my business in such an amazing manner without dama’s team!',
        name: 'Amir Wafiq',
        position: 'CEO, Ampio Foods',
        business: 'Tasty Bites',
        image: '/images/clients/AmirWafiq.png'
    },
    {
        quote: 'I wouldn’t launch my business in such an amazing manner without dama’s team!',
        name: 'Amir Wafiq',
        position: 'CEO, Ampio Foods',
        business: 'Tasty Bites',
        image: '/images/clients/AmirWafiq.png'
    },
]

const carousel: Ref<InstanceType<typeof Carousel> | null> = ref(null)

const scroll = (direction: number) => {
    if (carousel.value) {
        carousel.value.scroll(direction)
    }

}
</script>
<template>

    <div class="our-clients-container">
        <h1 class="sectionHeader">04. Our Clients</h1>

        <div class="our-clients-wrapper">
            <div class="left">
                <p class="sectionText">
                    We work with clients across the
                    entire globe to elevate their marketing game and drive real results.
                </p>
                <img src="/images/clients/behance.png" alt="Our Clients">
            </div>
            <div class="right">
                <Carousel ref="carousel" NoIndicator snap :numberOfItems="1" class="carousel">
                    <div class="client" v-for="(client, index) of clients" :key="index">
                        <div class="quote"><span class="large">“</span>
                            <p>{{ client.quote }}</p>
                        </div>
                        <div class="client-wrapper">
                            <div class="name-wrapper">
                                <div class="img">
                                    <img :src="client.image" :alt="client.name">

                                </div>
                                <div class="details">
                                    <span class="name">{{ client.name }}</span>
                                    <span class="position">{{ client.position }}</span>
                                </div>
                            </div>
                            <div class="bus">
                                <div>
                                    <span>{{ client.business }}</span>
                                </div>
                                <div class="arrows">
                                    <div class="left-arrow" @click="scroll(-1)">
                                        <svg width="25" height="16" viewBox="0 0 25 16" fill="none"
                                            xmlns="http://www.w3.org/2000/svg">
                                            <path
                                                d="M1 9C0.447715 9 4.82822e-08 8.55228 0 8C-4.82822e-08 7.44772 0.447715 7 1 7L1 9ZM24.7071 7.29289C25.0976 7.68342 25.0976 8.31658 24.7071 8.7071L18.3431 15.0711C17.9526 15.4616 17.3195 15.4616 16.9289 15.0711C16.5384 14.6805 16.5384 14.0474 16.9289 13.6569L22.5858 8L16.9289 2.34314C16.5384 1.95262 16.5384 1.31946 16.9289 0.928931C17.3195 0.538406 17.9526 0.538406 18.3431 0.928931L24.7071 7.29289ZM1 7L24 7L24 9L1 9L1 7Z"
                                                fill="#7B7B7B" />
                                        </svg>

                                    </div>
                                    <div class="right-arrow" @click="scroll(1)"><svg width="25" height="16"
                                            viewBox="0 0 25 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                                            <path
                                                d="M1 9C0.447715 9 4.82822e-08 8.55228 0 8C-4.82822e-08 7.44772 0.447715 7 1 7L1 9ZM24.7071 7.29289C25.0976 7.68342 25.0976 8.31658 24.7071 8.7071L18.3431 15.0711C17.9526 15.4616 17.3195 15.4616 16.9289 15.0711C16.5384 14.6805 16.5384 14.0474 16.9289 13.6569L22.5858 8L16.9289 2.34314C16.5384 1.95262 16.5384 1.31946 16.9289 0.928931C17.3195 0.538406 17.9526 0.538406 18.3431 0.928931L24.7071 7.29289ZM1 7L24 7L24 9L1 9L1 7Z"
                                                fill="#7B7B7B" />
                                        </svg>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </Carousel>

            </div>
        </div>

    </div>

</template>
<style lang="scss" scoped>
.our-clients-container {
    @include sectionPadding;

    .our-clients-wrapper {
        // display: flex;
        display: grid;
        padding: 1rem 0;
        gap: 2rem;
        // width:100%;
        grid-template-columns: 1fr 2fr;

        @media screen and (max-width: 768px) {
            grid-template-columns: 1fr;
            gap: 0;

        }

        .left {
            display: flex;
            flex-direction: column;
            justify-content: center;
            // align-items: center;
            gap: 3rem;
            padding: 3rem 0;
            // width:80rem;


            p {
                width: 80%;

                @media screen and (max-width: 768px) {
                    width: 100%;

                }
            }

            img {
                align-self: center;
            }

        }

        .right {
            .carousel {
                // background-color: red;
                // >*{
                //     width:30rem;
                // }
            }

            .client {
                width: 0;
                // background-color: red;
                padding: 3rem 0;
                display: flex;
                flex-direction: column;

                .large {
                    display: inline;
                }

                .quote {
                    font-size: 3rem;
                    font-weight: 800;
                    margin-bottom: 2rem;
                    padding-bottom: 2rem;
                    display: flex;
                    gap: 1rem;
                    span{
                        font-size: 5rem;
                        transform: translate(0, -0.3rem);
                    }

                    @media screen and (max-width: 425px) {
                        p {
                            font-size: 2rem;
                        }
                        span{
                            font-size: 3rem;
                        }

                    }



                }

                .client-wrapper {
                    // background-color: red;
                    display: inline-flex;
                    justify-content: space-between;
                    border-top: 1px solid lighten($grey, 10%);
                    padding-top: 2rem;
                    ;

                    @media screen and (max-width: 425px) {
                        // flex-direction: column;
                        gap: 2rem;

                    }

                    .name-wrapper {
                        display: flex;
                        gap: 1rem;
                        align-items: center;

                        .img {
                            border-radius: 100vh;
                            overflow: hidden;
                            display: flex;
                            align-items: center;
                            justify-content: center;

                            @media screen and (max-width: 425px) {
                                width: 4rem;
                                height: 4rem;

                            }

                            img {
                                width: 100%;
                                height: 100%;
                                object-fit: cover;
                            }
                        }

                        .details {
                            .name {
                                color: black;
                                font-size: 1.5rem;
                                font-weight: 600;
                            }

                            .position {
                                display: block;
                                margin-top: 0.2rem;
                                color: $grey;
                                font-size: 1rem;
                                font-weight: 400;
                            }
                        }

                    }

                    .bus {
                        color: $darkgrey;
                        font-size: 1rem;
                        font-weight: 600;
                        display: flex;
                        align-items: center;
                        gap: 1rem;

                        span {
                            display: block;
                        }

                        .arrows {
                            display: flex;
                            gap: 1rem;

                            .right-arrow,
                            .left-arrow {
                                display: flex;
                                align-items: center;
                                justify-content: center;
                                cursor: pointer;

                                &:hover {
                                    >svg>path {
                                        fill: black;
                                    }
                                }
                            }

                            .left-arrow {
                                transform: rotate(180deg);
                            }

                        }
                    }

                }
            }
        }
    }
}
</style>
