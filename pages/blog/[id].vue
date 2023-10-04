<template>
    <Head>
        <Title>benike.me | {{ post.title }}</Title>
    </Head>
    <div class="flex justify-center">
        <div class="w-1/3 rounded-lg p-4">
            <h1 class="text-4xl font-black text-center">{{ post.title }}</h1>
            <h2 class="text-xl font-black text-green-600 text-center">{{ formatDate(post.created) }}</h2>
            <h3 class="text-2xl font-black">{{ post.body }}</h3>
        </div>
    </div>
</template>

<script setup>
import PocketBase from 'pocketbase';

const pb = new PocketBase('https://benike.me/api');
const { id } = useRoute().params

const post = await pb.collection('posts').getOne(id);

if (!post) {
    throw createError({ statusCode: 404, message: 'Post not found', fatal: true })
}

const formatDate = (dateString) => {
  const date = new Date(dateString)
  const year = date.getFullYear()
  const month = date.getMonth() + 1
  const day = date.getDate()
  return `${year}.${month}.${day}`
}

definePageMeta({
    layout: 'blog',
    colorMode: 'dark',
})

</script>

<style lang="scss" scoped></style>