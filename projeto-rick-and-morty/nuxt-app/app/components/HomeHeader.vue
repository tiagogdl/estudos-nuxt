<template>
    <header class="px-4 xl:px-0 bg-fundoHeader w-full flex justify-center">
        <div class="max-w-[1224px] flex justify-between">
            <div class="grid gap-6">
                <div class="pt-4">
                    <img src="../public/images/LogoA.png" alt="Rick and Morry Dark" width="180">
                </div>

                <div class="flex flex-col gap-6">
                    <h1 class="font-bold text-5xl">Saiba tudo em um só <span class="text-text-blue">lugar.</span></h1>
                    <p>Personagens, localizações, episódios e muito mais.</p>
                </div>
                <div class="flex gap-3">
                    <button class="self-end bg-text-blue flex gap-2 py-[7px] px-2 rounded-[32px] text-white text-sm justify-center items-center w-[100px]" @click="dark = true">
                        <Moon />
                        Escuro
                    </button>
                    <button class="self-end bg-Son flex gap-2 py-[5px] px-2 rounded-[32px] text-white text-sm justify-center items-center w-[100px]" @click="dark = false">
                        <Son />
                        Claro
                    </button>
                </div>
                <p class="text-text-blue">{{ dark ? 'Ai sim, Porr#@%&*' : 'Wubba Lubba Dub Dub! Cuidado com os olhos.' }}</p>
            </div>

            <img v-if="dark" src="../public/images/HighlightImage.png" alt="Rick Escuro">
            <img v-else src="../public/images/imagelight.png" alt="Rick Claro" class="xl:px-42 p-0">
        </div>
    </header>
</template>

<script setup>
import {ref, watch} from 'vue';
import Moon from './icons/Moon.vue';
import Son from './icons/Son.vue';

const dark = ref(false)

watch(dark, function(value){
  document.documentElement.classList.toggle('dark', value)
})
</script>