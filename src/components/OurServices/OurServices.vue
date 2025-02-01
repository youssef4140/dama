<script setup lang="ts">
import { reactive } from 'vue';
import ServiceCard from './ServiceCard.vue';

const services = reactive([
    {
        title:'MARKETING SUPPORT',
        img:'/images/services/mobs.png',
        description:'We help businesses grow with tailored marketing strategies that deliver results. From social media management to performance analysis, we ensure your message reaches the right audience',
        tools:['Meta Ads Manager','Google Analytics','TikTok','VistaSocial','SEMrush'],
    },
    {
        title: 'DIGITAL PRODUCTS',
        img: '/images/services/polygons.png',
        description: "We`re driven by user-centered design that drives productivity and increases revenue. Our expertise and ingenuity are remarkable, yet We always stive to outdo and outperform our previous achievments.",
        tools: ['WordPress','Figma','Shopify','Blender','Adobe AfterEffects','Adobe Illustrator'],
    },
    {
        title: 'EVENT MANAGEMENT',
        img: '/images/services/rects.png',
        description: "We design and execute unforgettable events that leave lasting impressions. From corporate conferences to brand activations, we handle every detail to ensure seamless experiences.",
        tools: ['Activation Campaigns','Printables','Catering','Conferences','Seminars'],
    }
    
])

</script>

<template>
    <div class="section-container">

        <h1 class="sectionHeader">
            01- Our Services
        </h1>
        <p class="sectionText big">
            We go beyond marketing. We understand your challenges because <span class="blue">we’ve lived them,</span> delivering strategies that truly resonate with your <strong class="blue">business needs</strong>.
        </p>
        <div class="services-container">
            <ServiceCard v-for="service in services" :title="service.title" :img="service.img" :description="service.description" :tools="service.tools"  />
        </div>
    </div>
</template>

<style lang="scss" scoped>


.section-container{
    @include sectionPadding;
    display: flex;
    flex-direction: column;
    gap:2rem;

    p{
        @media screen and (min-width: 768px){
            max-width: 70%;
            
        }
    }

    .services-container{
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 5px;
    }
}
</style>