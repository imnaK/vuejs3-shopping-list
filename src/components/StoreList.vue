<script setup lang="ts">
import { inject, computed } from "vue";

const props = defineProps<{
  name: string,
  storeId: number,
}>();

const items: [{ id: number, storeId: number, name: string, completed: boolean; }] | null = inject("items") || null;

const storeItems = computed(() => {
  return items?.filter((item) => item.storeId == props.storeId);
});
</script>

<template>
  <div class="store-list">
    <h1>{{ props.name }}</h1>
    <ul v-if="storeItems && storeItems.length > 0">
      <li v-for="(item, index) in storeItems" :key="index" @click="item.completed = !item.completed">
        <input type="checkbox" v-model="item.completed">
        <h3 class="ml-1 mr-1">{{ item.name }}</h3>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.store-list {
  min-height: 8rem;
  width: 100%;
  background-color: var(--vt-c-primary);
  color: var(--vt-c-black);
  border-radius: var(--vt-c-border-radius);
  padding: 1rem;

  ul {
    list-style: unset;
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: .25rem;
    padding: unset;

    li {
      width: 100%;
      display: flex;
      align-items: center;
    }
  }
}
</style>