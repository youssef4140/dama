<script setup lang="ts">

const props = defineProps<{
    title: string;
    img: string;
    description: string;
    tools: string[];
}>()

</script>

<template>

<div class="service-wrapper" :style="{backgroundImage: `url(${img})`}">
    <h2>{{ title }}</h2>

    <div class="info">
        <p>{{ description }}</p>
        <ul>
            <li v-for="tool in tools">{{ tool }}</li>
        </ul>
    </div>
    
</div>

</template>

<style lang="scss" scoped>
.service-wrapper{
    // background-color: red;
    aspect-ratio: 1/1.1;
    border-radius: 5px;
    padding:1.5rem;
    background-size: 110%;
    background-position: center;
    // background-color: red;
    transition: background-size 0.5s ease-in-out;

    display: flex;
    flex-direction: column;
    justify-content: space-between;
    animation: breathe 2s infinite alternate;
    @keyframes breathe {
        0% {
            background-size: 115%;
        }
        100% {
            background-size: 125%;
        }
        
    }

    h2{
        color:white;
        font-size: 3rem;
        font-weight:500;
    }

    .info{
        p{
            color:white;
            font-size: 1.2rem;
            font-weight:400;
            padding-bottom:1rem;
            border-bottom: 2px solid white;
        }
        ul{
            list-style-type: none;
            display:flex;
            gap:5px;
            flex-wrap: wrap;
            margin-top:1rem;
            li{
                color:white;
                font-size: 0.8rem;
                font-weight:600;
                background-color: #d3d3c9;
                padding:5px 10px;
                border-radius: $radius;
                // padding:0.5rem 0;
                // border-bottom: 1px solid white;
            }
        }
    }
}
</style>