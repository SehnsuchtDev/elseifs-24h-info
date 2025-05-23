<template>
    <div class="w-75 max-w-md flex flex-col items-center justify-center">
        <div class="flex items-center mb-1 w-full justify-between">
            <button @click="decreaseBid" class="bg-gray-500 px-2 py-1 text-white rounded hover:bg-gray-700 cursor-pointer">-</button>
            <input readonly type="text" min="500000" :value="bidAmount + ' €'" class="mx-5 border-1 p-2 rounded text-center" />
            <button @click="increaseBid" class="bg-gray-500 px-2 py-1 text-white rounded hover:bg-gray-700 cursor-pointer">+</button>
        </div>
        <button @click="confirmBid" class="rounded bg-gray-500 px-4 py-2 font-bold text-white hover:bg-gray-700 cursor-pointer w-full">Proposer</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const bidAmount = ref(500000);

function increaseBid() {
    bidAmount.value += 1000;
}

function decreaseBid() {
    if (bidAmount.value > 0) {
        bidAmount.value -= 1000;
    }
}

function confirmBid() {

}
</script>