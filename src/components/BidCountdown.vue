<template>
  <div v-if="timeLeft > 0">
    <div class="text-red-500 font-bold">{{ hours }} heures {{minutes}} minutes {{ seconds }} secondes</div>
  </div>
  <div v-else>
    <span>Enchère terminée</span>
  </div>
</template>
<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

const targetDate = ref(new Date('2025-05-24T14:00:00Z')) 

const timeLeft = ref(getTimeLeft())

let timer = null

function getTimeLeft() {
  const now = new Date()
  return Math.max(0, targetDate.value - now)
}

const days = computed(() => Math.floor(timeLeft.value / (1000 * 60 * 60 * 24)))
const hours = computed(() => Math.floor((timeLeft.value / (1000 * 60 * 60)) % 24))
const minutes = computed(() => Math.floor((timeLeft.value / (1000 * 60)) % 60))
const seconds = computed(() => Math.floor((timeLeft.value / 1000) % 60))

onMounted(() => {
  timer = setInterval(() => {
    timeLeft.value = getTimeLeft()
  }, 1000)
})

onUnmounted(() => {
  clearInterval(timer)
})
</script>