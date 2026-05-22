<template>
    <section class="flex flex-col items-center xl:items-start gap-8">
            <SectionTitle>Episódios</SectionTitle>

            <div class="flex gap-4 flex-wrap justify-center lg:grid lg:grid-cols-[repeat(5,1fr)]">
                <DocumentCard v-for="currentEpisode in data.results"
                class="flex flex-col gap-2 justify-between h-[150px] max-w-[294px] xl:max-w-[250px]"
                >
                    <div class="flex gap-2 items-center">
                        <IconsPlay class="flex-[0_0_24px]"/>
                        <p>{{ currentEpisode.name }} | {{ currentEpisode.episode }}</p>
                    </div>
                    <div class="flex items-center justify-between">
                        <SaibaMais tipo="episode"/>
                        <IconsHearthFilled :width="32" :height="32"/>
                    </div>
                </DocumentCard>
            </div>
    </section>
</template>

<script setup>
const { data, status, error, refresh, clear } = await useFetch('https://rickandmortyapi.com/api/episode')

</script>