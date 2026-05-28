<template>
    <NuxtLink :to="urlType" class="self-end bg-text-blue flex gap-2 py-[6px] px-2 rounded-[32px] text-white text-sm items-center">
                <IconsInfo />
                Saiba Mais
    </NuxtLink>
</template>

<script setup>
const props = defineProps({
    id: Number,
    tipo: {
        type: String
    }
})

const urlType = computed(function(){
    if (props.tipo === 'character') {
        return `/character/${props.id}`
    } else if (props.tipo === 'episode'){
        return `/episode/${props.id}`
    } else if (props.tipo === 'location'){
        return `/location/${props.id}`
    }
})
</script>