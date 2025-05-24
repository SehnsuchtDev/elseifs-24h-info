<template>
    <div class="grid h-screen w-screen grid-cols-1 grid-rows-1">
        <div id="bidAlertList" class="absolute top-4 left-4">
            <BidAlert v-for="(alertData, idx) in bidAlerts" :key="idx" class="transition-all duration-300 ease-in-out"/>
        </div>
        <div class="flex flex-col bidCard flex rounded p-1 w-100 items-center justify-center shadow-md shadow-gray-700 bg-gray-700 place-self-center">
            <div class="text-xl w-full font-bold text-center">L'ampoule des frères Lumière</div>
            <img src="../assets/ampoule.jpg" alt="Ampoule des frères Lumière" width="100" height="100" class="" />
            <div class="text-base">Enchère actuelle : 500 000 €</div>
            <BidCountdown/>
            <button @click="placeBidForm" v-if="!displayBidForm" class="rounded bg-gray-500 px-4 py-2 font-bold text-white hover:bg-gray-700 cursor-pointer">Enchérir</button>
            <BidForm  v-if="displayBidForm"/>
            <div class="text-base text-justify">
                Cette ampoule rare a appartenu aux célèbres frères Lumière, pionniers du cinéma. Elle témoigne de l'ingéniosité et de l'histoire de l'éclairage au tournant du XXe siècle.
            </div>
        </div>
    </div>
</template>

<script setup>
import BidForm from './BidForm.vue'
import BidCountdown from './BidCountdown.vue'
import BidAlert from './BidAlert.vue'
import { ref } from 'vue'

import { onMounted } from 'vue'
const bidAlerts = ref([]);

onMounted(() => {
    function pushAlertIrregularly() {
        const delay = Math.random() * 5000 + 5000;
        setTimeout(() => {
            bidAlerts.value.push({});
            pushAlertIrregularly();
        }, delay);
    }
    pushAlertIrregularly();

    setInterval(() => {
        bidAlerts.value.shift();
    }, 3000);
});




const displayBidForm = ref(false);
function placeBidForm() {
    displayBidForm.value = !displayBidForm.value;

}

</script>
