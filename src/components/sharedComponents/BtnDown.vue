<script setup lang="ts">
import { ref } from 'vue';


const props=defineProps({
    width:{
        type:String,
        default:'5.5rem'
    },
    height:{
        type:String,
        default:'5.5rem'
    },
});

const getStyle=ref({
    width:props.width,
    height:props.height
});

</script>

<template>
 <div class="btn_down" :style="getStyle">
                    <div class="svg_fst">
                        <svg fill="#4541F0" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg"
                            xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 330 330" xml:space="preserve"
                            transform="rotate(0)" stroke="#4541F0">
                            <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
                            <g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"
                                stroke="#CCCCCC" stroke-width="0.66"></g>
                            <g id="SVGRepo_iconCarrier">
                                <path id="XMLID_30_"
                                    d="M154.394,325.606C157.322,328.535,161.161,330,165,330s7.678-1.465,10.607-4.394l75-75 c5.858-5.857,5.858-15.355,0-21.213c-5.858-5.857-15.356-5.857-21.213,0L180,278.787V15c0-8.284-6.716-15-15-15 c-8.284,0-15,6.716-15,15v263.787l-49.394-49.394c-5.858-5.857-15.355-5.857-21.213,0c-5.858,5.857-5.858,15.355,0,21.213 L154.394,325.606z">
                                </path>
                            </g>
                        </svg>
                    </div>
                    <div class="svg_snd">
                        <svg fill="#ffffff" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg"
                            xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 330 330" xml:space="preserve"
                            transform="rotate(0)" stroke="#ffffff">
                            <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
                            <g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"
                                stroke="#CCCCCC" stroke-width="0.66"></g>
                            <g id="SVGRepo_iconCarrier">
                                <path id="XMLID_30_"
                                    d="M154.394,325.606C157.322,328.535,161.161,330,165,330s7.678-1.465,10.607-4.394l75-75 c5.858-5.857,5.858-15.355,0-21.213c-5.858-5.857-15.356-5.857-21.213,0L180,278.787V15c0-8.284-6.716-15-15-15 c-8.284,0-15,6.716-15,15v263.787l-49.394-49.394c-5.858-5.857-15.355-5.857-21.213,0c-5.858,5.857-5.858,15.355,0,21.213 L154.394,325.606z">
                                </path>
                            </g>
                        </svg>
                    </div>
                </div>
</template>

<style lang="scss" scoped>
   .btn_down {
                background-color: $darkblue;
                border-radius: 50%;
                margin-right: 1rem;
                transition: all 0.3s ease-in-out;
                border: 2px solid white;
                padding: 1rem;
                position: relative;

                display: flex;
                justify-content: center;
                align-items: center;


                .svg_fst,
                .svg_snd {
                    position: absolute;
                    width: 50%;
                    transition: all 0.3s ease-in-out;

                }

                .svg_fst {
                    top: 40%;
                    left: 50%;
                    transform: translate(-50%, -50%);
                    transition: opacity 0;

                    opacity: 0;
                }

                &:hover {
                    border: 2px solid $darkblue;
                    background-color: white;
                    transition: all 0.3s ease-in-out;
                    transition: opacity 0;

                    .svg_fst {
                        top: 53%;
                        transition: all 0.3s ease-in-out;
                        transition: opacity 0;
                        opacity: 1;


                    }

                    .svg_snd {
                        transform: translateY(40%);
                        transition: opacity 0;

                        opacity: 0;
                    }

                }


            }
.btn_down {
    position: relative;


    &::after {
        content: '';
        position: absolute;
        top: 50%;
        left: 50%;
        width: 100%;
        height: 100%;
        border: 2px solid $darkblue;
        border-radius: 50%;
        transform: translate(-50%, -50%) scale(1);
        opacity: 0;
        animation: wave 2s ease-in-out infinite;
        animation-delay: 1s;
    }



    @keyframes wave {
        0% {
            transform: translate(-50%, -50%) scale(1);
            opacity: 0.5;
        }

        50% {
            transform: translate(-50%, -50%) scale(1.4);
            opacity: 0;
        }
    }
}
</style>