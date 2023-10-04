<template>
    <div class="flex flex-col h-screen items-center justify-center" :class="{ 'dark': isDarkMode }">
        <div class="flex flex-row text-center">
            <h1 :style="{ color: isDarkMode ? 'black' : 'white' }" class="font-black text-4xl p-4">benike.me</h1>
        </div>
        <div class="flex flex-row justify-center">
            <NuxtLink to="/blog">
                <Icon class="mr-2 ml-2" :class="{ 'dark:text-white': isDarkMode }" name="pixelarticons:avatar" :color="isDarkMode ? 'black' : 'white'" size="48px" />
            </NuxtLink>
            <a href="https://github.com/drinkmonster">
                <Icon class="mr-2 ml-2" :class="{ 'dark:text-white': isDarkMode }" name="pixelarticons:git-branch" :color="isDarkMode ? 'black' : 'white'" size="48px" />
            </a>
            <button class="mr-2 ml-2" @click="toggleDarkMode">
                <Icon :name="isDarkMode ? 'pixelarticons:sun' : 'pixelarticons:moon'" :color="isDarkMode ? 'black' : 'white'" size="48px" />
            </button>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const isDarkMode = ref(false);

function toggleDarkMode() {
  isDarkMode.value = !isDarkMode.value;
}

</script>

<style scoped>
.dark {
  background-color: #FFFFFF;
}
.dark .dark\\:text-white {
  color: white;
}
</style>
