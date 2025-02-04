<script setup lang="ts">
import AboutUs from '@/components/AboutUs/AboutUs.vue';
import Clients from '@/components/Clients/Clients.vue';
import HeroSection from '@/components/HeroSection/HeroSection.vue';
import OurClients from '@/components/OurClients/OurClients.vue';
import OurServices from '@/components/OurServices/OurServices.vue';
import Portfolio from '@/components/Portfolio/Portfolio.vue';
import TextCarousel from '@/components/TextCarousel/textCarousel.vue';

</script>

<template>
    <HeroSection />
    <TextCarousel />
    <OurServices />
    <AboutUs />
    <Clients/>
    <Portfolio/>
    <OurClients/>
</template>

<style lang="scss" scoped>
h1{}

</style>