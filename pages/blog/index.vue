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
        <div class="flex justify-center">
            <button v-if="currentPage > 1" @click="prevPage">Prev</button>
            <button v-if="currentPage < totalPages" @click="nextPage">Next</button>
        </div>
    </div>
</template>

<script setup>
import PocketBase from 'pocketbase';
import { ref, computed, onMounted } from 'vue';

const pb = new PocketBase('https://benike.me/api');
const posts = ref([]);
const search = ref('');
const currentPage = ref(1);
const perPage = ref(4);
const totalPosts = ref(0);

const totalPages = computed(() => {
    return Math.ceil(totalPosts.value / perPage.value);
});

const paginatedPosts = computed(() => {
    const start = (currentPage.value - 1) * perPage.value;
    const end = start + perPage.value;
    return posts.value.slice(start, end);
});

const filteredPosts = computed(() => {
    if (search.value === '') {
        return paginatedPosts.value;
    } else {
        return posts.value.filter(post => post.title.toLowerCase().includes(search.value.toLowerCase()));
    }
});

const prevPage = () => {
    currentPage.value--;
};

const nextPage = () => {
    currentPage.value++;
};

onMounted(async () => {
    posts.value = await pb.collection('posts').getFullList({
        sort: '-created',
    });
    totalPosts.value = posts.value.length;
});

definePageMeta({
    layout: 'blog',
    colorMode: 'dark',
})
</script>

<style lang="scss" scoped></style>