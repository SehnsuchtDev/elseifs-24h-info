<template>
    <div class="w-75 max-w-md flex flex-col items-center justify-center">
        <div class="flex items-center mb-1 w-full justify-between">
            <button @click="decreaseBid" class="bg-red-400 px-2 py-1 text-gray-700 rounded hover:bg-red-300 hover:text-gray-800 cursor-pointer">-</button>
            <input readonly type="text" min="500000" :value="bidAmount + ' €'" class="mx-5 border-1 p-2 rounded text-center" />
            <button @click="increaseBid" class="bg-green-400 px-2 py-1 text-gray-700 rounded hover:bg-green-300 hover:text-gray-800 cursor-pointer">+</button>
        </div>
        <button @click="confirmBid" class="rounded bg-yellow-400 px-4 py-2 font-bold text-gray-700 hover:bg-yellow-300 hover:text-gray-800 cursor-pointer w-full">Proposer</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const bidAmount = ref(500000);

function increaseBid() {
    if(bidAmount.value == "GROS RADIN") {
        bidAmount.value = 501000;
    }
    else {
        bidAmount.value += 1000;
    }
}

function decreaseBid() {
    if(bidAmount.value == "GROS RADIN") {
        bidAmount.value = 500000;
    }
    else if (bidAmount.value > 500000) {
        bidAmount.value -= 1000;
    }
    
}

function confirmBid() {
    if(bidAmount.value <= 501000) {
        bidAmount.value = 'GROS RADIN'
    }
    event.target.innerHtml = 'Merci'
}
</script>