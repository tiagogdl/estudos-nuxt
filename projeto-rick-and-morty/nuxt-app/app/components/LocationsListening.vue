<template>
    <section class="flex flex-col w-full max-w-[1224px] mx-auto gap-8 mt-20">
        <div class="flex flex-wrap gap-4 justify-center xl:justify-start">
            <SectionTitle :tipo="'locations'">Localizações</SectionTitle>
        </div>

         <div class="flex gap-4 flex-wrap justify-center lg:grid lg:grid-cols-[repeat(7,1fr)]">
                <DocumentCard v-for="currentLocation in data.results.slice(0, 7)"
                class="flex flex-col justify-between items-center h-[230px] max-w-[250px] xl:max-w-[250px]"
                >
                    <div class="flex flex-col gap-1 justify-center items-center text-center leading-tight">
                        <MundoLocation class="m-auto"/>
                        <p class="leading-tight">{{ currentLocation.type }}</p>
                        <p class="leading-tight text-text-blue">{{ currentLocation.name }}</p>
                    </div>
                    <div class="flex flex-col gap-3  items-center justify-between">
                        <SaibaMais :tipo="'location'" :id="currentLocation.id"/>
                        <IconsHearthFilled :width="32" :height="32"/>
                    </div>
                </DocumentCard>
            </div>
    </section>
</template>

<script setup>
import MundoLocation from './icons/MundoLocation.vue';

const { data, status, error, refresh, clear } = await useFetch('https://rickandmortyapi.com/api/location')
</script>