<template>
    <header class = "flex flex-row w-full bg-green-400 border-b-2 border-gray-400">
        <div class = "basis-1/4 items-center justify-start px-8"> 
            <img src="assets/images/logo2.jpg" class = "w-16 h-16 bg-transparent">
        </div>
        <div class = "basis-1/4">
        </div>
        <nav class = "basis-1/2 flex flex-row items-center justify-end px-8 gap-4">
            <NuxtLink href = "/" class = "my-auto p-2 hover:bg-gray-500 hover:text-white">Home</NuxtLink>
            <NuxtLink href = "/Lab3" class = "my-auto p-2 hover:bg-gray-500 hover:text-white">Lab3</NuxtLink>
            <NuxtLink href = "/login" class = "my-auto p-2 hover:bg-gray-500 hover:text-white">LogIn</NuxtLink>
            <NuxtLink href = "/logout" class = "my-auto p-2 hover:bg-gray-500 hover:text-white">LogOut</NuxtLink>
        </nav>
    </header>

    <main class = "p-5 flex bg-green-100 h-screen">
        <slot />
    </main>

    <footer class = "flex flex-row w-full bg-green-400 border-t-2 border-gray-400 items-center justify-center px-4 py-2 gap-4">
        <a href = "https://github.com/"><img src="assets/images/github.png" class="w-16 h-16"></img></a>
        <a href = "https://youtube.com/"><img src="assets/images/youtube.png" class="w-16 h-16"></img></a>
        <a href = "https://facebook.com/"><img src="assets/images/facebook.png" class="w-16 h-16 bg-transparent"></img></a>
    </footer>
</template>

<script setup lang="ts">
import { useHead } from "#app";
import { ref } from "vue";

useHead({
    script: [
        {
            async: true,
            src: 'https://www.googletagmanager.com/gtag/js?id=G-9BFTYEBPN7',
        },
        {
            innerHTML:`
            window.dataLayer = window.dataLayer || [];
            function gtag(){dataLayer.push(arguments);}
            gtag('js', new Date());
            gtag('config', 'G-9BFTYEBPN7');            
            `,
            type: 'text/javascript',
        },
    ],
    _dangerouslyDisableSanitizersByTagID: {
        gtag: ['innerHTML'],
    },
})

// const burger = ref<boolean>(false)
// const submenu = ref<boolean>(false)

// const switch_burger = ()=> (burger.value = !burger.value)
// const switch_submenu = ()=> (submenu.value = !submenu.value)

</script>