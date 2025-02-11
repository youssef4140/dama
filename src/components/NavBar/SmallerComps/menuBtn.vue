<script setup lang="ts">
import { ref } from 'vue';

const isActive = ref(false);
const emit = defineEmits(['toggleMenu']);
function toggleActive() {
    isActive.value = !isActive.value;
    emit('toggleMenu', isActive.value);
}
</script>

<template>
    <div :class="['btn-wrapper', { active: isActive }]" @click="toggleActive">
        <span></span><span></span><span></span>
    </div>
</template>

<style lang="scss" scoped>
.btn-wrapper {
    height: 100%;
    aspect-ratio: 1/1;
    padding: 1.8rem;
    // width:5rem;
    height: 100%;
    background-color: white;
    border: 1px solid $darkblue;
    border-radius: 100vh;
    position: relative;
    cursor: pointer;

    span {
        position: absolute;
        height: 4px;
        border-radius: 100vh;
        background: $darkblue;
        transition: all .4s ease-in-out .3s;

        // transition-property: width, left, top, transform;
        &:nth-child(1) {
            width: 0.7rem;
            transform: translatex(0%);
            left: 50%;
            top: 35%;
        }

        &:nth-child(2) {
            top: 50%;
            transform: translatex(-50%);
            left: 50%;
            width: 1rem;
        }

        &:nth-child(3) {
            width: 0.7rem;
            top: 62%;
            // transform: translateY(-100% );
            transform: translatex(-100%);
            left: 50%;
        }
    }

    &.active {
        background: white;

        >span {
            &:nth-child(1) {
                width: 1rem;
                top: 50%;
                left: 50%;
                // transform: translatex(-50%);


                // transform: rotate(45deg);
                transform:
                    rotate(45deg) translateX(-35%) translateY(0.33rem);


            }

            &:nth-child(2) {
                left: 0%;
                opacity: 0;
            }

            &:nth-child(3) {
                width: 1rem;
                top: 50%;

                left: 50%;
                transform:
                    rotate(-45deg) translateX(-35%) translateY(-0.33rem);

            }
        }
    }
}
</style>