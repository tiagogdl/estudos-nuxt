<template>
<section class="flex flex-col w-full max-w-[1224px] mx-auto gap-8">
  
      <div class="flex flex-wrap gap-4 justify-center xl:justify-start">
        <SectionTitle>
          Personagens
        </SectionTitle>

        <div class="flex flex-wrap gap-4 justify-center">
          <DocumentCard v-for="currentCharacter in data.results" class="max-w-[294px]">
              <img :src="currentCharacter.image" alt="Imagens personagens" height="200" width="262" class="rounded-2xl h-[200px] object-cover">
              <div class="grid grid-cols-[1fr,48px]">
                <div class="flex flex-col gap-4">
                  <p class="text-base font-bold">{{ currentCharacter.name }}</p>
                  <div class="flex flex-col gap-2">
                    <p>{{ currentCharacter.status === 'Alive' ? 'Vivo' : 'Morto' }}</p>
                    <p>{{ currentCharacter.species === 'Human' ? 'Humano' : 'Alienígena'}}</p>
                    <p>{{ currentCharacter.origin.name}}</p>
                  </div>
                </div>
                <div >
                  <IconsHearthFilled v-if="currentCharacter.status === 'Alive'" :width="48" :height="48" />
                  <IconsHearthOutlined v-else/>
                </div>
              </div>
              <SaibaMais :action-url="currentCharacter.url" class="mt-auto"/>
          </DocumentCard>
        </div>
      </div>
</section>
</template>

<script setup>
const { data, status, error, refresh, clear } = await useFetch('https://rickandmortyapi.com/api/character')
</script>