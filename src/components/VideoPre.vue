<script setup>
// Pas de logique spécifique pour l'instant
</script>

<template>
  <div class="min-h-screen text-white flex flex-col justify-center">
    <h1 class="text-5xl font-bold text-white text-center">
      Le spectacle des frères Lumière
    </h1>

    <article class="mt-[5vh] flex flex-col lg:flex-row justify-center items-start gap-[2vw] px-[10vw]">
      <!-- Image -->
      <img
        class="rounded-xl shadow-2xl max-w-full object-cover"
        style="width: 40vw; height: 50vh;"
        src="https://www.herodote.net/_images/antoine-lumiere.jpg"
        alt="Affiche du spectacle des frères Lumière"
      />

      <!-- Texte -->
      <div class="content bg-[#2B2927] rounded-xl p-8 w-full">
        <h2 class="text-2xl font-bold text-yellow-300 mb-2">
          Une première projection historique
        </h2>
        <p class="text-lg leading-relaxed mb-6">
          Le 28 décembre 1895, les frères Lumière organisent à Paris la toute première projection publique payante de cinéma au Salon Indien du Grand Café, boulevard des Capucines. Cet événement marque la naissance officielle du cinéma tel que nous le connaissons.
        </p>

        <h2 class="text-2xl font-bold text-yellow-300 mb-2">
          Les films présentés
        </h2>
        <p class="text-lg leading-relaxed mb-6">
          Lors de cette séance, une dizaine de courts films sont projetés, dont le célèbre "Sortie de l’usine Lumière à Lyon", "L’Arroseur arrosé" et "L’Arrivée d’un train en gare de La Ciotat". Ces séquences de quelques dizaines de secondes fascinent le public par leur réalisme et leur mouvement.
        </p>

        <h2 class="text-2xl font-bold text-yellow-300 mb-2">
          Un succès retentissant
        </h2>
        <p class="text-lg leading-relaxed">
          La séance est un triomphe. Le public est émerveillé, parfois même effrayé, comme lors de l’arrivée du train filmé. Ce moment fondateur va déclencher un engouement mondial pour le cinéma, faisant des frères Lumière des pionniers incontestés de cet art naissant.
        </p>
      </div>
    </article>
  </div>
</template>

<style scoped>
/* Personnalise ici si besoin */
</style>