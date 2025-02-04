<script setup lang="ts">






import { onMounted } from 'vue';









let circles: NodeListOf<HTMLElement>;

const move = (dot: HTMLElement, direction: number = 1) => {
    const angle = parseInt(dot.dataset.position as string);
    const to = parseInt(dot.dataset.to as string);
    let currentAngle = angle;
    let animationFrameId: number;


    let speed = (Math.abs((to - angle))/90) *3;

    const animate = () => {
        currentAngle += direction * speed;
        // console.log((currentAngle % 360 - to) , speed);
        const coords = getCircleEdgeCoordinates(currentAngle);
        dot.style.left = `${coords.x}%`;
        dot.style.top = `${coords.y}%`;
        // console.log(currentAngle, to);
        if (Math.abs(currentAngle % 360 - to) <= speed) {
            cancelAnimationFrame(animationFrameId);
            return;
        }
        animationFrameId = requestAnimationFrame(animate);
        dot.dataset.animationFrameId = animationFrameId.toString();
    };

    animationFrameId = requestAnimationFrame(animate);
}

const unmove = (dot: HTMLElement) => {
    cancelAnimationFrame(Number(dot.dataset.animationFrameId));
    const angle = parseInt(dot.dataset.position as string);
    const coords = getCircleEdgeCoordinates(angle);
    dot.style.left = `${coords.x}%`;
    dot.style.top = `${coords.y}%`;
}

const toggleActivity = (e: MouseEvent) => {
    // console.log(circles)
    const index = Array.from(circles).indexOf(e.target as HTMLElement);
    circles.forEach((circle, i) => {
        if (i > index) {
            circle.classList.toggle('active');
        }

        if (i === index) {
            circle.querySelectorAll('.dot.data').forEach((dot) => {
                dot.classList.toggle('moves');
                if (dot.classList.contains('moves')) {
                    const direction = parseInt(((dot as HTMLElement).dataset.direction as string)) | 1;
                    move(dot as HTMLElement, direction);
                } else {
                    unmove(dot as HTMLElement);
                }
            });
        }


        // console.log(`Width: ${circle.offsetWidth}, Height: ${circle.offsetHeight}`);


    });
}

function getCircleEdgeCoordinates(angle: number) {

    const radians = angle * (Math.PI / 180);

    const x = 50 + 50 * Math.cos(radians);
    const y = 50 + 50 * Math.sin(radians);

    return { x, y };
}


onMounted(() => {
    circles = document.querySelectorAll('[data-circle]') as NodeListOf<HTMLElement>;
    circles.forEach((circle) => {
        const dot = circle.querySelectorAll('.dot.main') as NodeListOf<HTMLElement>;
        dot.forEach((dot) => {
            const angle = parseInt(dot.dataset.position as string);
            const coords = getCircleEdgeCoordinates(angle);
            dot.style.left = `${coords.x}%`;
            dot.style.top = `${coords.y}%`;

        });
        // const angle = parseInt(dot.dataset.position as string);
        // const coords = getCircleEdgeCoordinates(angle);
        // dot.style.left = `${coords.x}%`;
        // dot.style.top = `${coords.y}%`;

    });
});

</script>
<template>
    <div class="circle-cont">
        <div class="circle"></div>
        <div class="circle_1" data-circle @mouseenter="toggleActivity($event)" @mouseleave="toggleActivity($event)">
            <div class="dot main" data-position="133">
                <span>Product</span>
            </div>

            <div class="dot data" data-position="133" data-to="210" data-direction="1"><span>Optimization</span></div>
            <div class="dot data" data-position="133" data-to="175" data-direction="1"><span>Experiments</span></div>
            <div class="dot data" data-position="133" data-to="90" data-direction="-1"><span>A/B Testing</span></div>

        </div>
        <div class="circle_2" data-circle @mouseenter="toggleActivity($event)" @mouseleave="toggleActivity($event)">
            <div class="dot main" data-position="133">
                <span>Insights</span>

            </div>
            <div class="dot data" data-position="133" data-to="210" data-direction="1"><span>Innovation</span></div>
            <div class="dot data" data-position="133" data-to="175" data-direction="1"><span>User Experience</span>
            </div>
            <div class="dot data" data-position="133" data-to="90" data-direction="-1"><span>Visual Design</span></div>
            <div class="dot data" data-position="133" data-to="45" data-direction="-1"><span>Development</span></div>



        </div>
        <div class="circle_3" data-circle @mouseenter="toggleActivity($event)" @mouseleave="toggleActivity($event)">
            <div class="dot main" data-position="313">
                <span>Growth</span>


            </div>
            <div class="dot data" data-position="-47" data-to="223" data-direction="1"><span>UX Strategy</span></div>
            <div class="dot data" data-position="-47" data-to="90" data-direction="1"><span>Data Science</span></div>
            <div class="dot data" data-position="-47" data-to="150" data-direction="1"><span>UX Research</span></div>



        </div>

    </div>
</template>
<style lang="scss" scoped>
.circle-cont {

    // height: 32rem;
    width: 90vw;
    aspect-ratio: 1/1;
    border-radius: 100vh;
    background-color: transparent;
    position: relative;
    // overflow: hidden;
    @media screen and (min-width: 768px) {
        width:32vw;
        
    }

    .dot {
        background-color: black;
        width: 0.6rem;
        height: 0.6rem;
        border-radius: 100vh;
        position: absolute;
        z-index: 1;
        // transition: all 0.1s;
        // transform: translate(-50%, 0%);

        transform: translate(-50%, -50%);


        &.main {
            background-color: #1b76ff;
            width: 0.9rem;
            height: 0.9rem;
            transform: translate(-50%, -50%);


            &::after {
                content: '';
                position: absolute;
                top: 50%;
                left: 50%;
                width: 100%;
                height: 100%;
                background-color: grey;
                // border: 2px solid #1b76ff;
                border-radius: 50%;
                // transform: translate(-50%, -50%) scale(1);
                opacity: 0;
                animation: wave 1s linear infinite;
                // animation-delay: 1s;



                @keyframes wave {
                    0% {
                        transform: translate(-50%, -50%) scale(1);
                        opacity: 0.3;
                    }

                    100% {
                        transform: translate(-50%, -50%) scale(4);
                        opacity: 0;
                    }
                }

            }
        }

        &.data {
            height: 0.3rem;
            width: 0.3rem;
            border-radius: 0;
            background-color: transparent;

            span {
                display: none;
            }

            &.moves {
                background-color: black;

                span {
                    display: block;

                }
            }
        }

        span {
            position: absolute;
            top: -2rem;
            left: 1rem;
            font-size: 1rem;
            font-weight: 500;

        }

    }

    >div {
        border-radius: 100vh;
        aspect-ratio: 1/1;
    }

    .circle {
        width: 100%;
        height: 100%;
        background-color: #f4f4f4;

        border-radius: 100vh;
        position: absolute;
        top: 0%;
        right: 0%;


    }

    .circle_1 {
        width: 85.4%;
        // height: 70%;
        background-color: #eee;
        position: absolute;
        top: 2.13812%;
        right: 2.13812%;
        cursor: pointer;



    }

    .circle_2 {
        width: 68.14%;
        // height: 70%;
        background-color: #e1e1e1;
        position: absolute;
        top: 4.66%;
        right: 4.66%;
        cursor: pointer;


    }

    .circle_3 {
        width: 42%;
        // height: 70%;
        background-color: #f4f4f4;
        position: absolute;
        top: 8.5%;
        right: 8.5%;
        cursor: pointer;


    }

    .circle_1,
    .circle_2,
    .circle_3 {
        text-align: center;
        transition: all 0.5s;
        border: 1px solid transparent;


        &:hover {
            border-color: rgb(204, 200, 200);
        }
    }

    .active {
        opacity: 0.5;
    }
}
</style>