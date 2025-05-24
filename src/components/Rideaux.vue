<script setup>
import SpotLight from './SpotLight.vue'
import { onMounted, ref, computed } from 'vue'


const midScreenYpx = ref(0);
const midScreenVH = ref(0);
window.addEventListener('scroll',function(e) {
    midScreenYpx.value = window.scrollY + window.screen.height/2;
    midScreenVH.value = window.scrollY / window.screen.height + 0.5;
});


const los_freros = computed(() => {
    return midScreenVH.value > 0.75;
})

const spotLightTarget = computed(() => {
    console.log(midScreenVH.value);
    return {
        y: (1.5 - midScreenVH.value) * window.screen.height,
        x: window.screen.width/2
    }
})

</script>

<template>
    
    <SpotLight v-if="los_freros"
    :targetPosition="spotLightTarget"
    :originPosition="{x: 50, y: 0}"
    :spotlightRadius="150"
    :featherAmount="50"
    color="#fff8"
/>
<div class="night-overlay" :style="{opacity: (los_freros?0.7:1)}"></div>
<main>
    
<img src="../assets/ridal.png" alt="Rideaux" class="w-full h-screen object-stretch" />

<img class="freres" :style="{zIndex: (los_freros?1500:1)}" src="../assets/fratelli_lumierini.png" alt="Fratelli Lumière" />
</main>
</template>

<style scoped>
main {
    background-color: #0a0007;
    background-image: url("https://www.transparenttextures.com/patterns/45-degree-fabric-light.png");
    min-height: 200vh;
    width: 100%;
}

.night-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    z-index: 100;
    }
.freres {
    position: absolute;
    top: 75vh;
    left: 50%;
    transform: translate(-50%, 0);
}    
</style>
