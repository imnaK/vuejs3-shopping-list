<script setup lang="ts">
const props = defineProps<{
  name: string,
}>();
</script>

<template>
  <div class="shopping-list-card">
    <h3>{{ name }}</h3>
  </div>
</template>

<style lang="scss" scoped>
.shopping-list-card {
  min-height: 8rem;
  width: 100%;
  background-color: var(--color-background-soft);
  border-radius: var(--vt-c-border-radius);
  padding: 1rem;
  cursor: pointer;
}
</style>