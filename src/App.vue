<script setup>
import BidCard from './components/BidCard.vue'
import Presentation from './components/Presentation.vue';
import Rideaux from './components/Rideaux.vue';
</script>

<template>
    <div class="main-container">
        <Rideaux />
        <Presentation />
        <BidCard />
    </div>
</template>

<style scoped>
.main-container {
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>
