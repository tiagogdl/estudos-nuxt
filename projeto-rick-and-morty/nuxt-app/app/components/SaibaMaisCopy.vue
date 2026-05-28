<template>
    <NuxtLink :to="url" class="self-end bg-text-blue flex gap-2 py-[6px] px-2 rounded-[32px] text-sm items-center">
                <IconsInfo />
                Saiba Mais
    </NuxtLink>
</template>

<script setup>
const props = defineProps({
    url: {
        String
    }
})
</script>