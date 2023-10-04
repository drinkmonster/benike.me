<template>
    <Head>
        <Title>benike.me | Blog</Title>
    </Head>
    <div>
        <h1 class="text-center text-4xl font-black pb-4">Blog</h1>
        <div class="flex justify-center" v-for="post in posts">
            <BlogCard :post="post" />
        </div>
    </div>
</template>

<script setup>
import PocketBase from 'pocketbase';

const pb = new PocketBase('https://benike.me/api');
const posts = await pb.collection('posts').getFullList({
    sort: '-created',
});
definePageMeta({
    layout: 'blog',
})
</script>

<style lang="scss" scoped></style>