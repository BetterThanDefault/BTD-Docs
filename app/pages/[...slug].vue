<script setup lang="ts">
const route = useRoute()
const path = route.path === '/' ? '/index' : route.path

const { data: page } = await useAsyncData(route.path, () =>
  queryCollection('docs').path(path).first()
)
</script>

<template>
  <UContainer class="py-10">
    <ContentRenderer v-if="page" :value="page" />
    <div v-else>
      <h1>Not found</h1>
      <p>No doc at {{ route.path }}</p>
    </div>
  </UContainer>
</template>
