<template>
  <div>
    <h1 class="text-purple-600">Código ao Ponto</h1>

    <div class="flex w-full-max-w-[1224px] gap-4 mx-auto">
      <div v-for="currentCharacter in data.results">
          <img :src="currentCharacter.image" alt="Imagens personagens">
          <p>{{ currentCharacter.name }}</p>
          <p>{{ currentCharacter.status }}</p>
          <p>{{ currentCharacter.species }}</p>
          <p>{{ currentCharacter.origin.name}}</p>

          
      </div>
    </div>
  </div>
</template>
<script setup>
const { data, status, error, refresh, clear } = await useFetch('https://rickandmortyapi.com/api/character')

console.log(data.value)

</script>