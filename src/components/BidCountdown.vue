<template>
    <div v-if="timeLeft > 0" class="flex items-center gap-2">
        <div class="flex items-center gap-2 bg-white rounded-lg shadow px-4 py-2 border border-gray-200">
            <span class="text-gray-700 font-semibold text-lg">
                {{ hours.toString().padStart(2, '0') }}
            </span>
            <span class="text-xs text-gray-400">h</span>
            <span class="text-gray-700 font-semibold text-lg">
                {{ minutes.toString().padStart(2, '0') }}
            </span>
            <span class="text-xs text-gray-400">m</span>
            <span class="text-gray-700 font-semibold text-lg">
                {{ seconds.toString().padStart(2, '0') }}
            </span>
            <span class="text-xs text-gray-400">s</span>
        </div>
    </div>
    <div v-else class="flex items-center gap-2">
        <span class="bg-gray-100 text-gray-400 rounded-lg px-4 py-2 text-sm font-medium border border-gray-200">Enchère terminée</span>
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