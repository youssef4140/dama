<script setup lang="ts">
const props = defineProps<{
    isActive: boolean;
}>();

</script>

<template>
    <div class="btn-wrapper" :class="{'active': isActive}" >
        <div class="background"></div>

        <div class="transition-wrapper">
            <span class="fst">+ Become a client</span>
            <span class="snd">+ Become a client</span>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.btn-wrapper {
    display: flex;
    align-items: center;
    // flex-direction: column;
    padding: 1.2rem 1.5rem;
    // height:100%;
    background-color: white;
    border: 1px solid $darkblue;
    border-radius: $radius;
    transition: all 0.5s;
    overflow: hidden;
    cursor: pointer;
    color: black;
    font-weight: 400;
    font-size: 1rem;
    position: relative;

    @media screen and (max-width: 375px) {
        padding: 1rem;
        font-size: 0.7rem;

    }

    .background {
        background-color: $darkblue;
        position: absolute;
        top: 0;
        right: 100%;
        width: 100%;
        height: 100%;
        border-radius: $radius;
        transition: all 0.5s;


    }

    .transition-wrapper {
        position: relative;
        overflow: hidden;



        .fst {
            display: block;
            transition: all 0.5s;
            color: $darkblue;


        }

        .snd {
            color: white;

            position: absolute;
            top: 100%;
            left: 0;
            transition: all 0.5s;

        }
    }



    &:hover {
        // background-color: $darkblue;

        .background {
            right: 0;
            transition: all 0.5s;

        }

        .transition-wrapper {
            .fst {
                transform: translatey(-100%);
                transition: all 0.5s;

            }

            .snd {
                top: 0;
                transition: all 0.5s;

            }
        }
    }

    &.active {
        background-color: white;
        .background{
            background-color: $lilac;
        }
        .transition-wrapper {
         
            .snd {
                color: $darkblue;
            }
        }
    }
        
}
</style>