<template>
    <section class="flex flex-col w-full max-w-[1224px] mx-auto gap-8 mt-8">
        <div class="px-4 xl:px-0 flex justify-between items-center">
            <img src="/public/images/LogoA.png" alt="" class="py-10">
             <button
                @click="voltar"
                class="bg-text-blue flex py-[8px] px-6 rounded-[32px] text-sm items-center text-white"
                >
                Voltar
            
            </button>
        </div>
            <h1 class="text-5xl font-bold mb-16 text-shadow-sm text-center">Episódios</h1>

            <div class="flex gap-4 flex-wrap justify-center lg:grid lg:grid-cols-[repeat(5,1fr)]">
                <DocumentCard v-for="currentEpisode in data.results"
                class="flex flex-col gap-2 justify-between h-[150px] max-w-[294px] xl:max-w-[250px]"
                >
                    <div class="flex gap-2 items-start">
                        <IconsPlay class="flex-[0_0_24px]"/>
                        <p>{{ currentEpisode.name }} | {{ currentEpisode.episode }}</p>
                    </div>
                    <div class="flex items-center justify-between">
                        <SaibaMais :tipo="'episode'" :id="currentEpisode.id" />
                        <IconsHearthFilled :width="32" :height="32"/>
                    </div>
                </DocumentCard>
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
import { ref, computed } from 'vue';
const router = useRouter()

const voltar = () => {
  router.back()
}
const page = ref(1)
const { data, status, error, refresh, clear } = await useFetch(() => `https://rickandmortyapi.com/api/episode?page=${page.value}` , {
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