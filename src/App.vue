<script setup lang="ts">
import { ref, provide } from "vue";
import ShoppingListCard from "./components/ShoppingListCard.vue";

const selectedListId = ref(-1);

let tblListsIdCounter = 0;
const tblLists = ref([
  { id: tblListsIdCounter++, name: "Liste1" },
  { id: tblListsIdCounter++, name: "Coole Liste" },
  { id: tblListsIdCounter++, name: "Wieso ist hier der name so lang? Doch noch länger? Ich kann hier aber echt viel Text rein schreiben lol!" },
]);

let tblStoresIdCounter = 0;
const tblStores = ref([
  { id: tblStoresIdCounter++, listId: 0, name: "Edeka" },
  { id: tblStoresIdCounter++, listId: 0, name: "Rewe" },
  { id: tblStoresIdCounter++, listId: 0, name: "Penny" },
  { id: tblStoresIdCounter++, listId: 1, name: "Aldi" },
  { id: tblStoresIdCounter++, listId: 1, name: "Lidl" },
  { id: tblStoresIdCounter++, listId: 2, name: "Netto" },
]);

let tblItemsIdCounter = 0;
const tblItems = ref([
  { id: tblItemsIdCounter++, storeId: 0, name: "Tomaten", completed: false },
  { id: tblItemsIdCounter++, storeId: 0, name: "Gurken", completed: false },
  { id: tblItemsIdCounter++, storeId: 0, name: "Sauce Hollandaise", completed: false },
  { id: tblItemsIdCounter++, storeId: 0, name: "Schinken", completed: false },
  { id: tblItemsIdCounter++, storeId: 1, name: "Brot", completed: false },
  { id: tblItemsIdCounter++, storeId: 1, name: "Baguette de Baguette", completed: false },
]);

provide("selectedListId", selectedListId);
provide("lists", tblLists);
provide("stores", tblStores);
provide("items", tblItems);

</script>

<template>
  <header></header>

  <main>
    <h1>Einkaufslisten</h1>
    <div class="list-cards">
      <ShoppingListCard v-for="list in tblLists" :key="list.id" :name="list.name" @click="selectedListId = list.id" />
    </div>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

.list-cards {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(16rem, 1fr));
  grid-gap: 1rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
