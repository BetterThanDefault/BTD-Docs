<script setup lang="ts">
const { data: page } = await useAsyncData('home', async () => {
  // try "/" first, then "/index" (Nuxt Content v3 can differ)
  return (await queryCollection('docs').path('/').first())
      ?? (await queryCollection('docs').path('/index').first())
})
</script>

<template>
  <UContainer class="py-10">
    <ContentRenderer v-if="page" :value="page" />
    <div v-else>
      <h1>Not found</h1>
      <p>Couldn't find content for / or /index</p>
    </div>
  </UContainer>
</template>
