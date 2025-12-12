<script setup lang="ts">
const { data, error } = await useAsyncData('docs', () =>
  queryCollection('docs').all()
)
</script>

<template>
  <UContainer class="py-10">
    <h1>Docs collection items</h1>
    <p>error: {{ error ? error.message : 'none' }}</p>
    <pre>{{ data ?? '<<undefined>>' }}</pre>
  </UContainer>
</template>
