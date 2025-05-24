<template>
    <div class="grid h-screen grid-cols-3 items-start mt-20">
        <!-- Alerts -->
        <div id="bidAlertList" class="col-start-1 p-4">
            <BidAlert v-for="(alertData, idx) in bidAlerts" :key="idx" class="transition-all duration-300 ease-in-out"/>
        </div>
        <!-- Bid Card -->
        <div
            class="col-start-2 flex flex-col items-center justify-center rounded-2xl p-6 w-[420px] shadow-2xl shadow-gray-900 bg-gradient-to-b from-gray-700 via-gray-800 to-gray-900 border border-gray-700 ring-2 ring-yellow-400/30 place-self-center"
        >
            <div class="text-2xl w-full font-extrabold text-center mb-2 text-yellow-300 drop-shadow-lg tracking-wide">
                L'ampoule usagée des frères Lumière
            </div>
            <img
                src="../assets/ampoule.jpg"
                alt="Ampoule des frères Lumière"
                width="140"
                height="140"
                class="rounded-full shadow-lg border-4 border-yellow-400 mb-4 bg-gray-200 object-cover"
            />
            <div class="text-lg font-semibold text-yellow-200 mb-2">
                Enchère actuelle : <span class="text-yellow-400 font-bold">500 000 €</span>
            </div>
            <BidCountdown class="mb-3"/>
            <button
                @click="placeBidForm"
                v-if="!displayBidForm"
                class="rounded-full bg-yellow-400 px-6 py-2 font-bold text-gray-900 shadow hover:bg-yellow-300 cursor-pointer transition-colors duration-200 mb-3"
            >
                Enchérir
            </button>
            <BidForm v-if="displayBidForm" class="w-full mb-3"/>
            <div class="text-base text-justify text-gray-200 bg-gray-700/60 rounded-lg p-4 mt-2 shadow-inner">
                Cette ampoule rare a appartenu aux célèbres frères Lumière, pionniers du cinéma. Elle témoigne de l'ingéniosité et de l'histoire de l'éclairage au tournant du XXe siècle.
            </div>
        </div>
    </div>
</template>

<script setup>
import BidForm from './BidForm.vue'
import BidCountdown from './BidCountdown.vue'
import BidAlert from './BidAlert.vue'
import { ref, onMounted } from 'vue'

const bidAlerts = ref([]);

onMounted(() => {
    function pushAlertIrregularly() {
        const delay = Math.random() * 5000 + 5000;
        setTimeout(() => {
            bidAlerts.value.push({});
            pushAlertIrregularly();
            setTimeout(() => {
                bidAlerts.value.shift();
            }, 7000);
        }, delay);
    }
    pushAlertIrregularly();
});

const displayBidForm = ref(false);
function placeBidForm() {
    displayBidForm.value = !displayBidForm.value;
}
</script>
