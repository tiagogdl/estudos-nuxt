<template>
<PageContainer>
    <div class="px-20 flex flex-col justify-center items-center">
        <div class="px-4 xl:px-0 flex w-screen xl:w-full justify-between items-center">
            <img src="/public/images/LogoA.png" alt="" class="py-10">
             <button
                @click="voltar"
                class="bg-text-blue flex py-2 px-6 rounded-4xl text-sm items-center text-white"
                >
                Voltar
            
            </button>
        </div>

        <div class="flex gap-64">
            <div class="flex flex-col xl:flex-row gap-16">
                <img :src="data.image" alt="Foto Personagem" width="369" height="461" class="rounded-2xl">
                <div class="flex flex-col gap-12">
                    <div class="flex gap-4 justify-between">
                        <h1 class="text-3xl xl:text-5xl xl:whitespace-nowrap">{{ data.name }} </h1>
                        <div class="mt-1" >
                            <IconsHearthFilled v-if="data.status === 'Alive'" :width="48" :height="48" />
                            <IconsHearthOutlined :width="48" :height="48" v-else/>
                        </div>
                    </div>
                    <p class="flex"><Play :width="24" :height="24" class="mr-1"/> Participou de {{ data.episode.length }} {{ data.episode.length == 1 ? 'episódio' : 'episódios' }}</p>
                    <div class="flex gap-6">
                        <p class="flex"><Pulse class="mt-1 mr-1" />{{ data.status === 'Alive' ? 'Vivo' : 'Morto' }}</p>
                        <p class="flex"><Alien class="mt-1 mr-1"/>{{ data.species === 'Human' ? 'Humano' : 'Alienígena'}}</p>
                        <p class="flex"><VectorGender class="mt-1 mr-1"/>{{ data.gender === 'Male' ? 'Homem' : 'Mulher' }}</p>
                    </div>
                </div>
            </div>

            <div class="items-end gap-16 hidden xl:flex">
                <div class="flex items-center justify-center gap-10">
                    <DocumentCard
                        class="flex flex-col justify-between items-center h-[220px] min-w-[170px] max-w-[200px] xl:max-w-[200px] gap-0"
                        >
                            <div class="flex flex-col gap-1 justify-center items-center text-center leading-tight">
                            <MundoLocation class="m-auto mb-4" />
                            <p class="leading-tight">{{ data.origin.name }}</p>
                
                            </div>
                            <div class="flex flex-col gap-3  items-center justify-between">
                                <SaibaMais />
                                <IconsHearthFilled :width="32" :height="32"/>
                            </div>
                        </DocumentCard>
                        <DocumentCard
                        class="flex flex-col justify-between items-center h-[220px] min-w-[170px] max-w-[200px] xl:max-w-[200px]"
                        >
                            <div class="flex flex-col gap-1 justify-center items-center text-center leading-tight">
                                <MapIn class="m-auto mb-2"/>
                                <p class="leading-tight">{{ data.location.name }}</p>
                
                            </div>
                            <div class="flex flex-col gap-3  items-center justify-between">
                                <SaibaMais />
                                <IconsHearthFilled :width="32" :height="32"/>
                            </div>
                        </DocumentCard>
                </div>
            </div>
        </div>
    </div>
</PageContainer>
</template>

<script setup>
import Alien from '~/components/icons/Alien.vue';
import HearthFilled from '~/components/icons/HearthFilled.vue';
import HearthOutlined from '~/components/icons/HearthOutlined.vue';
import MapIn from '~/components/icons/MapIn.vue';
import MundoLocation from '~/components/icons/MundoLocation.vue';
import Play from '~/components/icons/play.vue';
import Pulse from '~/components/icons/Pulse.vue';
import VectorGender from '~/components/icons/VectorGender.vue';

const route = useRoute()
const router = useRouter()

const voltar = () => {
  router.back()
}

const { data, status, error, refresh, clear } = await useFetch(`https://rickandmortyapi.com/api/character/${route.params.id}`)

console.log(data)

useHead({
    title: `${data.value.name} - Rick And Morty`,

    link: [{rel: "icon", type: "image/x-icon", href: data.value.image
    }]
})
</script>