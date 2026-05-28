<template>
<PageContainer>
    <div class="xl:px-20 mb-20 flex flex-col justify-center">
        <div class="px-4 xl:px-0 flex w-screen xl:w-full justify-between items-center">
            <img src="/public/images/LogoA.png" alt="" class="py-10">
             <button
                @click="voltar"
                class="bg-text-blue flex gap-2 py-[8px] px-6 rounded-[32px] text-sm items-center text-white"
                >
                Voltar
            
            </button>
        </div>
        <div class="flex gap-64 justify-center px-4 xl:p-0 xl:justify-start">
            <div>
                <Play width="50" height="50" class="mb-3"/>
                <div class="flex flex-col gap-6">
                    <div class="flex gap-4 ">
                        <h1 class="text-5xl ">{{ data.name }} </h1>
                        <HearthOutlined class="mt-1" width="70" height="50" />
                    </div>
                    <div class="flex">
                        <p class="flex"><CalendarBlank width="18" height="18" class="mt-1 mr-1" /> {{ data.air_date }} </p>
                        <p class="flex ml-4"><Queue width="18" height="18" class="mt-1 mr-1"/> {{ data.episode }}</p>
                    </div>
                    <div class="mt-4">
                        <p class="flex"><Smiley width="18" height="18" class="mt-1 mr-1" /> {{ data.characters.length }} Personagens participaram desse episódio</p>
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
import Play from '~/components/icons/play.vue';
import Queue from '~/components/icons/Queue.vue';
import Smiley from '~/components/icons/Smiley.vue';


const route = useRoute()
const router = useRouter()

const voltar = () => {
  router.back()
}

const { data, status, error, refresh, clear } = await useFetch(`https://rickandmortyapi.com/api/episode/${route.params.id}`)

console.log(data)

useHead({
    title: `Rick And Morty`,

    link: [{rel: "icon", type: "image/x-icon"
    }]
})
</script>
