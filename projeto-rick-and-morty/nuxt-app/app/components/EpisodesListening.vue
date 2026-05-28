<template>
    <section class="flex flex-col w-full max-w-[1224px] mx-auto gap-8 mt-20">
            <div class="flex flex-wrap gap-4 justify-center xl:justify-start">
                <SectionTitle :tipo="'episodes'">Episódios</SectionTitle>
            </div>

            <div class="flex gap-4 flex-wrap justify-center lg:grid lg:grid-cols-[repeat(5,1fr)]">
                <DocumentCard v-for="currentEpisode in data.results.slice(0, 5)"
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
    </section>
</template>

<script setup>
const { data, status, error, refresh, clear } = await useFetch('https://rickandmortyapi.com/api/episode')

</script>