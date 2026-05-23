<template>
    <div>
        <img src="/public/images/LogoA.png" alt="" class="py-10">
        <div class="flex gap-16" >
            <img :src="data.image" alt="Foto Personagem" width="369" height="461" class="rounded-2xl">
            <div class="flex flex-col gap-12">
                <h1 class="text-5xl">{{ data.name }}</h1>
                <p>Participou de {{ data.episode.length }} episódios</p>
                <div class="flex gap-6">
                    <p>{{ data.status === 'Alive' ? 'Vivo' : 'Morto' }}</p>
                    <p>{{ data.species === 'Human' ? 'Humano' : 'Alienígena'}}</p>
                    <p>{{ data.gender === 'Male' ? 'Homem' : 'Mulher' }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const route = useRoute()

const { data, status, error, refresh, clear } = await useFetch(`https://rickandmortyapi.com/api/character/${route.params.id}`)

useHead({
    title: `${data.value.name} - Rick And Morty`,

    link: [{rel: "icon", type: "image/x-icon", href: data.value.image
    }]
})
</script>