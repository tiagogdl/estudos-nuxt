<template>
  <div class="text-white">
    <h1 class="text-purple-600">Código ao Ponto</h1>

    <div class="flex flex-wrap w-full max-w-[1224px] gap-4 mx-auto">
      <div v-for="currentCharacter in data.results" class="bg-[#313234] rounded-lg flex flex-col gap-4 p-4">
          <img :src="currentCharacter.image" alt="Imagens personagens" height="200" width="262" class="rounded-2xl">

          <div class="grid grid-cols-[1fr,48px]">
            <div class="flex flex-col gap-4">
              <p class="text-base font-bold">{{ currentCharacter.name }}</p>

              <div class="flex flex-col gap-2">
                <p>{{ currentCharacter.status === 'Alive' ? 'Vivo' : 'Morto' }}</p>
                <p>{{ currentCharacter.species === 'Human' ? 'Humano' : 'Alienígena'}}</p>
                <p>{{ currentCharacter.origin.name}}</p>
              </div>
            </div>

            <span>
              <svg width="48" height="48" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M45 17.625C45 30.75 25.5394 41.3737 24.7106 41.8125C24.4922 41.93 24.248 41.9915 24 41.9915C23.752 41.9915 23.5078 41.93 23.2894 41.8125C22.4606 41.3737 3 30.75 3 17.625C3.00347 14.5429 4.22936 11.5881 6.40872 9.40872C8.58808 7.22936 11.5429 6.00347 14.625 6C18.4969 6 21.8869 7.665 24 10.4794C26.1131 7.665 29.5031 6 33.375 6C36.4571 6.00347 39.4119 7.22936 41.5913 9.40872C43.7706 11.5881 44.9965 14.5429 45 17.625Z" fill="#11B0C8"/></svg>
            </span>
          </div>

          <NuxtLink :to="currentCharacter.url" class="mt-2">Saiba Mais</NuxtLink>
      </div>
    </div>
  </div>
</template>
<script setup>
const { data, status, error, refresh, clear } = await useFetch('https://rickandmortyapi.com/api/character')

console.log(data.value)

</script>