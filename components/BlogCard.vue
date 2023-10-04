<template>
    <div class="w-1/3 rounded-lg p-4">
        <h1 class="text-4xl font-black">{{ post.title }}</h1>
        <h2 class="text-xl font-black text-green-600">{{ formatDate(post.created) }}</h2>
        <h3 class="text-2xl font-black truncate mb-2">{{ post.body }}</h3>
        <NuxtLink class="p-2 bg-stone-900 hover:bg-stone-950 rounded-lg py-2" :to="`/blog/${post.id}`">
            View full post
        </NuxtLink>
    </div>
</template>

<script setup>
const { post } = defineProps(['post'])

const formatDate = (dateString) => {
  const date = new Date(dateString)
  const year = date.getFullYear()
  const month = date.getMonth() + 1
  const day = date.getDate()
  return `${year}.${month}.${day}`
}
</script>

<style lang="scss" scoped></style>