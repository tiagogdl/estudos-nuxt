<template>
   <div
   class="flex flex-col gap-16">
      <HomeHeader />
   <PageContainer>
     <CharactersListening />
      <EpisodesListening />
      <LocationsListening />
   </PageContainer>
   </div>
</template>
<script setup>
import PageContainer from '~/layouts/PageContainer.vue';


useHead({
    title: `Rick And Morty`
})
</script>