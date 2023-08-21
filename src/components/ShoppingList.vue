<script setup lang="ts">
import { ref } from "vue";
import ShoppingListCard from "./ShoppingListCard.vue";

let id = 0;

const shoppingLists = ref([
  { id: id++, name: "Liste1" },
  { id: id++, name: "Coole Liste" },
  { id: id++, name: "Wieso ist hier der name so lang?" },
]);
</script>

<template>
  <div>
    <h1>Einkaufslisten</h1>
    <div class="shopping-lists">
      <ShoppingListCard v-for="shoppingList in shoppingLists" :key="shoppingList.id" :name="shoppingList.name" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.shopping-lists {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(16rem, 1fr));
  grid-gap: 1rem;
}
</style>