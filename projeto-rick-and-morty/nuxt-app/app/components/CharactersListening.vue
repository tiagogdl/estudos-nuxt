<template>
<section class="flex flex-col w-full max-w-[1224px] mx-auto gap-8 mt-20">
  
      <div class="flex flex-wrap gap-4 justify-center xl:justify-start">
        <SectionTitle :tipo="'characters'">
          Personagens
        </SectionTitle>

        <div class="flex flex-wrap gap-4 justify-center">
          <DocumentCard v-for="currentCharacter in data.results.slice(0, 8)" class="max-w-[294px]">
              <img :src="currentCharacter.image" alt="Imagens personagens" height="200" width="262" class="rounded-2xl h-[200px] object-cover">
              <div class="grid grid-cols-[1fr,48px]">
                <div class="flex flex-col gap-4">
                  <div class="flex justify-between">
                    <p class="text-base font-bold mt-2">{{ currentCharacter.name }}</p>
                    <div class="flex">
                      <IconsHearthFilled v-if="currentCharacter.status === 'Alive'" :width="48" :height="48" />
                      <IconsHearthOutlined :width="48" :height="48" v-else/>
                    </div>
                  </div>
                  <div class="flex flex-col gap-2">
                    <p class="flex "><Pulse class="mt-1 mr-1"/> {{ currentCharacter.status === 'Alive' ? 'Vivo' : 'Morto' }}</p>
                    <p class="flex"> <Alien class="mt-1 mr-1"/>{{ currentCharacter.species === 'Human' ? 'Humano' : 'Alienígena'}}</p>
                    <p class="flex"> <Planet class="mt-1 mr-1" />{{ currentCharacter.origin.name}}</p>
                  </div>
                </div>
              </div>
              <SaibaMais :tipo="'character'" :id="currentCharacter.id" class="mt-auto"/>

          </DocumentCard>
        </div>
      </div>
</section>
</template>

<script setup>
import Alien from './icons/Alien.vue';
import Planet from './icons/Planet.vue';
import Pulse from './icons/Pulse.vue';

const { data, status, error, refresh, clear } = await useFetch('https://rickandmortyapi.com/api/character')
</script>