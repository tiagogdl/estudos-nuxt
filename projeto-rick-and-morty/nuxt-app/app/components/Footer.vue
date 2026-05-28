<template>
    <footer class="flex flex-col items-center px-4 py-20 ">
        <div class="py-6 flex justify-between w-full ">
            <img src="../public/images/LogoA.png" alt="Logo Rick And Morty">
            <BackTop />
        </div>
        <div class="border-t-2 w-screen pb-3"></div>
        <div class="flex justify-between py-6 w-full">
            <p>&copy; {{ new Date().getFullYear() }}</p>

            <p>
                <i class="fa-solid fa-angle-left text-text-blue"></i>
                <i class="fa-solid fa-angle-right text-text-blue"></i>

                 Desenvolvido por <a href="https://github.com/tiagogdl" class="text-text-blue font-bold">Tiago Dias</a></p>
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