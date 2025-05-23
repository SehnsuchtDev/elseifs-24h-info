<template>
    <div class="flex h-screen w-screen items-center justify-center border-solid border-red-100">
        <div class="flex flex-col bidCard flex rounded border-1 p-1 w-100 items-center justify-center">
            <div class="text-xl">L'ampoule des frères lumière</div>
            <img src="../assets/ampoule.jpg" alt="Ampoule des frères lumière" width="100" height="100" class="" />
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
import { ref } from 'vue'


const displayBidForm = ref(false);
function placeBidForm() {
    displayBidForm.value = !displayBidForm.value;

}

</script>
