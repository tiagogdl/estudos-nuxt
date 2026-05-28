<template>
<PageContainer>
    <div class="xl:px-20 mb-20">
        <div class="w-screen xl:w-full xl:px-0 px-4 flex justify-between items-center">
            <img src="/public/images/LogoA.png" alt="" class="py-10">
             <button
                @click="voltar"
                class="bg-text-blue flex gap-2 py-[8px] px-6 rounded-[32px] text-sm items-center text-white"
                >
                Voltar
            
            </button>
        </div>
        <div class="flex gap-64 justify-center xl:justify-start">
            <div>
                <MundoLocation class="mb-6  "/>
                <div class="flex flex-col gap-8">
                    <div class="flex gap-4">
                        <h1 class="text-4xl xl:text-5xl whitespace-nowrap">{{ data.name }} </h1>
                        <HearthOutlined class="mt-1" width="70" height="50" />
                    </div>
                    <div class="flex">
                        <p class="flex"><Planet class="mt-1 mr-1" /> {{ data.type}} </p>
                        <p class="flex ml-4"><VectorCaixa :width="18" class=" mr-1"/>{{ data.dimension }}</p>
                    </div>
                    <div class="mt-4">
                        <p class="flex"><Smiley width="18" height="18" class="mt-1 mr-1" /> {{ data.residents.length }}  Personagens localizados aqui</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</PageContainer>
</template>

<script setup>
import CalendarBlank from '~/components/icons/CalendarBlank.vue';
import HearthOutlined from '~/components/icons/HearthOutlined.vue';
import MundoLocation from '~/components/icons/MundoLocation.vue';
import Planet from '~/components/icons/Planet.vue';
import Play from '~/components/icons/play.vue';
import Queue from '~/components/icons/Queue.vue';
import Smiley from '~/components/icons/Smiley.vue';
import VectorCaixa from '~/components/icons/VectorCaixa.vue';


const route = useRoute()
const router = useRouter()

const voltar = () => {
  router.back()
}

const { data, status, error, refresh, clear } = await useFetch(`https://rickandmortyapi.com/api/location/${route.params.id}`)

console.log(data)

useHead({
    title: `Rick And Morty`,

    link: [{rel: "icon", type: "image/x-icon"
    }]
})
</script>
