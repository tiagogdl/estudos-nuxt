<template>
    <header class="flex gap-4">
          <h2 class="font-bold text-2xl"><slot></slot></h2>
      
          <NuxtLink :to="urlType" class="flex gap-2 py-[6px] px-2 bg-verTodos rounded-[32px] text-white">
            <IconsSquaresFour/>
            Ver todos
          </NuxtLink>
        </header>
</template>

<script setup>

const props = defineProps({
  tipo: {
        type: String
    }
})
const urlType = computed(function(){
    if (props.tipo === 'characters') {
        return `/characters/`
    } else if (props.tipo === 'episodes'){
        return `/episodes/`
    } else if (props.tipo === 'locations'){
        return `/locations/`
    }
})
</script>