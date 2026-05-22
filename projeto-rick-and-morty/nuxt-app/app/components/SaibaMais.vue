<template>
    <NuxtLink :to="urlType" class="self-end bg-[#11B0C8] flex gap-2 py-[6px] px-2 rounded-[32px] text-sm items-center">
                <IconsInfo />
                Saiba Mais
    </NuxtLink>
</template>

<script setup>
const props = defineProps({
    id: Number,
    tipo: {
        type: String,
        default: 'character'
    }
})

const urlType = computed(function(){
    if (props.tipo === 'character') {
        return `/character/${props.id}`
    } else if (props.tipo === 'episode'){
        return `/episode/${props.id}`
    } else {
        return `/location/${props.id}`
    }
})
</script>