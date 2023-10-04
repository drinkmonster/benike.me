<template>
    <Head>
        <Title>benike.me</Title>
    </Head>
    <div class="flex flex-col h-screen items-center justify-center">
        <div class="flex flex-row text-center">
            <h1 class="font-black text-4xl p-4">benike.me</h1>
        </div>
        <div class="flex flex-row justify-center">
            <NuxtLink to="/blog">
                <Icon class="mr-2 ml-2" name="pixelarticons:avatar" color="white" size="48px" />
            </NuxtLink>
            <a href="https://github.com/drinkmonster">
                <Icon class="mr-2 ml-2" name="pixelarticons:git-branch" color="white" size="48px" />
            </a>
        </div>
    </div>
</template>

<script setup>
definePageMeta({
  colorMode: 'dark',
})
</script>

<style scoped>

</style>
