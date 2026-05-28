<template>
    <section class="flex flex-col w-full max-w-[1224px] mx-auto gap-8 mt-8">
      <div class="px-4 xl:px-0 flex justify-between items-center px-4">
            <img src="/public/images/LogoA.png" alt="" class="py-10">
             <button
                @click="voltar"
                class="bg-text-blue flex py-[8px] px-6 rounded-[32px] text-sm items-center text-white"
                >
                Voltar
            
            </button>
        </div>
      <div class="flex flex-wrap gap-4 justify-center">
        <h1 class="text-5xl font-bold mb-16 text-shadow-sm">Personagens</h1>
        <div class="flex flex-wrap gap-4 justify-center">
          <DocumentCard v-for="currentCharacter in data.results" class="max-w-[294px]">
              <img :src="currentCharacter.image" alt="Imagens personagens" height="200" width="262" class="rounded-2xl h-[200px] object-cover">
              <div class="grid grid-cols-[1fr,48px]">
                <div class="flex flex-col gap-4">
                  <div class="flex justify-between">
                    <p class="text-base font-bold mt-2">{{ currentCharacter.name }}

                    </p>
                    <div >
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
      <div class="flex justify-center gap-8">
            <button class="self-end bg-text-blue flex gap-2 py-[8px] px-6 rounded-[32px] text-sm items-center text-white"
            @click="prevPage"
            :disabled="page === 1"

            >
                Anterior
            </button>

            <span class="mt-1 font-bold text-xl rounded-full p-1 border border-text-blue">{{ page }}</span>

            <button class="self-end bg-text-blue flex gap-2 py-[8px] px-6 rounded-[32px] text-sm items-center text-white"
            @click="nextPage"
            :disabled="!data?.info?.next"
            >
                Próxima
            </button>
        </div>
</section>
</template>

<script setup>
import { ref, watch} from 'vue';
import Alien from '~/components/icons/Alien.vue';
import Planet from '~/components/icons/Planet.vue';
import Pulse from '~/components/icons/Pulse.vue';
const router = useRouter()

const voltar = () => {
  router.back()
}

const page = ref(1)
const { data, status, error, refresh, clear } = await useFetch(() => `https://rickandmortyapi.com/api/character?page=${page.value}` , {
    watch: [page]
})

const nextPage = function() {
    if (data.value?.info?.next) 
    page.value++;
};

const prevPage = function() {
    if (page.value > 1) 
    page.value--;
};


</script>