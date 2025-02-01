<script setup lang="ts">
import { onMounted } from 'vue';


function getCircleEdgeCoordinates(containerWidth:number, containerHeight:number, angle:number) {
  const radius = Math.min(containerWidth, containerHeight) / 2;
  const centerX = containerWidth / 2;
  const centerY = containerHeight / 2;

  // Convert angle to radians
  const radians = angle * (Math.PI / 180);

  // Calculate x and y on the circle's edge
  const x = centerX + radius * Math.cos(radians);
  const y = centerY + radius * Math.sin(radians);

  return { x, y };
}

// Example usage
onMounted(() => {
  const div = document.getElementById('circularDiv') as HTMLElement;
  const smallCircle = document.getElementById('smallCircle') as HTMLElement;
  const angle = 0; // Angle in degrees
  console.log(div.offsetWidth, div.offsetHeight, angle);
  const coords = getCircleEdgeCoordinates(div.offsetWidth, div.offsetHeight, angle);
  smallCircle.style.left = `${coords.x}px`;
  smallCircle.style.top = `${coords.y}px`;
});


</script>
<template>
   <div id="circularDiv">
    <div id="smallCircle"></div>
   </div>
</template>
<style lang="scss" scoped>
#circularDiv {
  position: relative;
  width: 200px;
  height: 200px;
  border-radius: 100vh;
  background-color: lightblue;
  #smallCircle {
    position: absolute;
    width: 20px;
    height: 20px;
    border-radius: 100vh;
    background-color: red;
    transform: translate(-50%, -50%);
  }
}

</style>