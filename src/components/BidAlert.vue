<template>
    <transition name="fade" mode="out-in">
    <div class="bg-red-400 p-2 rounded flex items-center mb-2 w-fit max-w-full">
       <button class="cursor-pointer hover:bg-gray-500/50 bg-gray-500/20 rounded p-1 px-2 mr-2 font-bold">X</button>
       <div>{{name}} a proposé {{bid}} €</div>
    </div>
    </transition>
</template>

<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>

<script setup>

const nameList = [
    "Jean",
    "Marcel",
    "Henri",
    "Georges",
    "André",
    "René",
    "Albert",
    "Louis",
    "Paul",
    "Raymond"
];

let name = nameList[Math.floor(Math.random() * nameList.length)];
let bid = 500000 + Math.floor(Math.random() * 1000000);

</script>