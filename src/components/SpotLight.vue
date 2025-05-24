<script setup>
import { useSSRContext } from 'vue';
import { computed } from 'vue';
const props = defineProps({
  color: {
    type: String,
    default: "#fff4"
  },
  targetPosition: {
    type: Object
  },
  originPosition: {
    type: Object,
    default: {x:400,y:0}
  },
  spotlightRadius: {
    type: Number,
    default: 150 // pixels
  },
  featherAmount: {
    type: Number,
    default: 50 // pixels
  }
})

const usefull = computed(() => 
{
  return {
    distance: Math.sqrt(Math.pow(props.targetPosition.y-props.originPosition.y,2)+Math.pow(props.targetPosition.x-props.originPosition.x,2)),
  }
})


const spotGradient = computed(() => {
  const featherFactor = Math.max(0.7,Math.min(1.,usefull.value.distance/500))
  const YscaleFactor = Math.max(1.,Math.min(1.2, usefull.value.distance/500))
  return {
  x: props.targetPosition.x+"px",
  y: props.targetPosition.y+"px",
  scaleX: '100',
  scaleY: 100*YscaleFactor,
  color: props.color,
  hardLightRadius: props.spotlightRadius-featherFactor*props.featherAmount+"px",
  fullRadius: props.spotlightRadius+featherFactor*props.featherAmount*0.5+"px"
}});

const spotGradientCSS = computed(()=>`radial-gradient(${spotGradient.value.scaleX}px ${spotGradient.value.scaleY}px at ${spotGradient.value.x} ${spotGradient.value.y}, ${spotGradient.value.color} ${spotGradient.value.hardLightRadius}, #0000 ${spotGradient.value.fullRadius})`);

const conicGradient =  computed(() => {
  const adj = usefull.value.distance
  const opp = props.spotlightRadius+props.featherAmount
  const hyp = Math.sqrt(opp*opp + adj*adj)
  const sangle = Math.acos(adj/hyp)
  return {
  x: props.originPosition.x+"px",
  y: props.originPosition.y+"px",
  color: props.color,
  angle: Math.PI/2 + Math.atan2((props.targetPosition.y-props.originPosition.y),props.targetPosition.x-props.originPosition.x),
  semi_angle: sangle

}});

const conicGradientCSS = computed(()=>`conic-gradient(from ${conicGradient.value.angle}rad at ${conicGradient.value.x} ${conicGradient.value.y}, ${conicGradient.value.color} 1deg,#0000 ${conicGradient.value.semi_angle}rad, #0000 ${(2*Math.PI)-conicGradient.value.semi_angle}rad,${conicGradient.value.color}`);

const conicClip = computed(() => `circle(${usefull.value.distance+0.850*props.spotlightRadius}px at ${props.originPosition.x}px ${props.originPosition.y}px)`)

</script>

<template>
 <div class="spotlight spot" :style="{background: spotGradientCSS}">

 </div>
 <div class="spotlight" :style="{background: conicGradientCSS, clipPath: conicClip, opacity: 0.5}">

 </div>
</template>

<style scoped>
  .spotlight {
    position: fixed;
    top: 0;
    left: 0;
    width:100%;
    height: 100%;
    background-repeat: repeat-y;
    mix-blend-mode: add;
    /*clip-path: circle(200px);*/
    filter: blur();
    z-index: 1000;
  }
  .spot {
    animation: 1.3s infinite alternate-reverse both running spot-opa;
  }

@keyframes spot-opa {
  0% {
    opacity: 90%
  }
  10% {
    opacity: 100%
  }
  45% {
    opacity: 90%
  }
  57% {
    opacity: 100%
  }
  100% {
    opacity:100%
  }
}
</style>