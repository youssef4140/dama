<script setup lang="ts">
import { onMounted, onUnmounted, ref, type Ref } from 'vue';
import Carousel from '../sharedComponents/Carousel.vue';

const portfolio = [
    {
        title: 'UI UX Design And Web Development for Identity UAE website',
        desc: `An architectural and interior design firm based in the UAE and operating worldwide. We have delivered a number of creative interiors for hospitality, healthcare, office, retail and residential spaces, from design concept to handover.`,
        image: '/images/portfolio/1.png'
    },
    {
        title: 'Personal Branding & Rebranding for Klinics - Dr Karim Fahmy',
        desc: `Founded by Dr. Karim Fahmy, a renowned dentist with over 15 years of experience and a Fellow of the Royal College of Surgeons (RCS) England and Royal College of Physicians and Surgeons of Glasgow (RCPSG).`,
        image: '/images/portfolio/2.png'
    },
    {
        title: 'Product & Marketing Support  for  e-learning Platform Blanoia LTD',
        desc: `Blanoia is an online platform offering specialized training and consultation in engineering and business administration.`,
        image: '/images/portfolio/3.png'
    },
]

const numberOfCarouselItems = ref(1);
const updateCarouselItems = () => {
    const isMobile = window.matchMedia('(max-width: 768px)').matches
    const isDesktop = window.matchMedia('(min-width: 1024px)').matches

    if (isMobile) {
        numberOfCarouselItems.value = 1
    } else if (isDesktop) {
        numberOfCarouselItems.value = 3
    } else {
        numberOfCarouselItems.value = 2
    }
}

const carousel: Ref<InstanceType<typeof Carousel> | null> = ref(null)

const scroll = (direction:number) => {
    if (carousel.value) {
        carousel.value.scroll(direction)
    }

}

onMounted(() => {
    updateCarouselItems()
    window.addEventListener('resize', updateCarouselItems)
})

onUnmounted(() => {
    window.removeEventListener('resize', updateCarouselItems)
})

</script>

<template>

    <div class="portfolio-container">
        <h1 class="sectionHeader-m">03. Portfolio</h1>

        <div class="portfolio-wrapper">
            <div class="header">
                <p class="small">Our <br> Portfolio</p>
                <p class="big">Latest<br> Cases</p>
            </div>

            <Carousel snap :numberOfItems="numberOfCarouselItems" NoIndicator ref="carousel">
                <div class="portfolio" v-for="p of portfolio" :key="p.title">
                    <div class="portfolio-image">
                        <img :src="p.image" alt="Portfolio Image">
                    </div>
                    <div class="content">
                        <h3>{{ p.title }}</h3>
                        <p>{{ p.desc }}</p>
                    </div>

                </div>
            </Carousel>
            <div class="carousel-btns">
                <div class="left" @click="scroll(-1)"><svg width="17" height="26" viewBox="0 0 17 26" fill="none"
                        xmlns="http://www.w3.org/2000/svg">
                        <path d="M14 3L3.74619 12.9431C3.33883 13.3381 3.3414 13.9925 3.75186 14.3843L12.7778 23"
                            stroke="white" stroke-width="5" stroke-linecap="round" />
                    </svg>
                </div>
                <div class="bar"></div>
                <div class="right" @click="scroll(1)"><svg width="17" height="26" viewBox="0 0 17 26" fill="none"
                        xmlns="http://www.w3.org/2000/svg">
                        <path d="M3 3L13.2538 12.9431C13.6612 13.3381 13.6586 13.9925 13.2481 14.3843L4.22222 23"
                            stroke="white" stroke-width="5" stroke-linecap="round" />
                    </svg>

                </div>
            </div>

        </div>

    </div>
</template>

<style lang="scss" scoped>
.portfolio-wrapper {
    margin-top: 2rem;
    background-image: url('/images/portfolio/portfolioBackground.png');
    width: 100%;
    // height: 100vh;
    padding: 3rem;

    >.header {

        margin-bottom: 3rem;

        >p {
            &.small {
                color: $grey;
                font-size: 1.5rem;
                font-weight: 500;
            }

            &.big {
                font-size: 3rem;
                font-weight: 700;
                color: white;
            }
        }
    }
}

.portfolio {



    width: 50%;

    @media screen and (max-width: 425px) {
        width: 100%;

    }

    @media screen and (min-width: 1024px) {
        width: 33%;
    }

    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .content {
        margin-top: 1rem;
        color: white;

        h3 {
            font-size: 1.7rem;
        }

        p {
            margin-top: 1rem;
            font-size: 1.2rem;
            font-weight: 200;
        }
    }

}

.carousel-btns {
    margin-top: 2rem;
    display: flex;
    align-items: center;
    gap:6px;
    // justify-content: center;
    @media screen and (max-width: 768px) {
        justify-content: center;
        
    }

    .left,
    .right {
        cursor: pointer;

        &:hover{
            >svg>path{
                stroke: $grey;
            }
        }

    }

    .bar{
        width: 5rem;
        height: 5px;
        border-radius: 100vh;
        background-color: white;
    }

}
</style>