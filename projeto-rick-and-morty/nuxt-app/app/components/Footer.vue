<template>
    <footer class="flex flex-col items-center">
        <div class="py-20 flex justify-between w-full">
            <img src="../public/images/LogoA.png" alt="Logo Rick And Morty">
            <BackTop />
        </div>
        <div class="border-t-2 flex justify-between py-6 w-full">
            <p>&copy; {{ new Date().getFullYear() }}</p>

            <p>
                <i class="fa-solid fa-angle-left text-[#11B0C8]"></i>
                <i class="fa-solid fa-angle-right text-[#11B0C8]"></i>

                 Desenvolvido por <a href="https://github.com/tiagogdl" class="text-[#11B0C8] font-bold">Tiago Dias</a></p>
        </div>
    </footer>
    
</template>

<script setup>
useHead({
    script: [
        {
            src: "https://kit.fontawesome.com/3f74b64bc3.js",crossorigin:"anonymous"
        }
    ]
})
</script>