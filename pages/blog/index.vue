<template>
    <Head>
        <Title>benike.me | Blog</Title>
    </Head>
    <div class="flex flex-col justify-center">
        <h1 class="text-center text-4xl font-black pb-4">Blog</h1>
        <input class="self-center p-4" type="text" placeholder="Search..." v-model="search">
        <div class="flex justify-center" v-for="post in filteredPosts">
            <BlogCard :post="post" />
        </div>
    </div>
</template>

<script setup>
import PocketBase from 'pocketbase';
import { ref, computed } from 'vue';

const pb = new PocketBase('https://benike.me/api');
const posts = await pb.collection('posts').getFullList({
    sort: '-created',
});
const search = ref('');

const filteredPosts = computed(() => {
    return posts.filter(post => post.title.toLowerCase().includes(search.value.toLowerCase()));
});

definePageMeta({
    layout: 'blog',
})
</script>

<style lang="scss" scoped></style>