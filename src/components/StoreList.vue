<script setup lang="ts">
import { inject } from "vue";

const props = defineProps<{
  name: string,
}>();

const items: [{ id: number, storeId: number, name: string, completed: boolean; }] | null = inject("items") || null;
</script>

<template>
  <div class="store-list">
    <h1>{{ props.name }}</h1>
    <ul v-if="items && items.length > 0">
      <li v-for="(item, index) in items" :key="index">
        {{ item.name }}
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.store-list {
  min-height: 8rem;
  width: 100%;
  background-color: var(--color-background-soft);
  border-radius: var(--vt-c-border-radius);
  padding: 1rem;
}
</style>