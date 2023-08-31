<script setup lang="ts">
import { ref, reactive, provide } from "vue";
import ShoppingList from "./components/ShoppingList.vue";
import StoreList from "./components/StoreList.vue";

const selectedListId = ref(-1);

let tblListsIdCounter = 0;
const tblLists = reactive([
  { id: tblListsIdCounter++, name: "Liste1" },
  { id: tblListsIdCounter++, name: "Coole Liste" },
  { id: tblListsIdCounter++, name: "Wieso ist hier der name so lang? Doch noch länger? Ich kann hier aber echt viel Text rein schreiben lol!" },
]);

let tblStoresIdCounter = 0;
const tblStores = reactive([
  { id: tblStoresIdCounter++, listId: 0, name: "Edeka" },
  { id: tblStoresIdCounter++, listId: 0, name: "Rewe" },
  { id: tblStoresIdCounter++, listId: 0, name: "Penny" },
  { id: tblStoresIdCounter++, listId: 1, name: "Aldi" },
  { id: tblStoresIdCounter++, listId: 1, name: "Lidl" },
  { id: tblStoresIdCounter++, listId: 2, name: "Netto" },
]);

type typeItem = { id: number, storeId: number, name: string, completed: boolean; };
let tblItemsIdCounter = 0;
const tblItems: typeItem[] = reactive([
  { id: tblItemsIdCounter++, storeId: 0, name: "Tomaten", completed: false },
  { id: tblItemsIdCounter++, storeId: 1, name: "Gurken", completed: true },
  { id: tblItemsIdCounter++, storeId: 2, name: "Sauce Hollandaise", completed: false },
  { id: tblItemsIdCounter++, storeId: 3, name: "Schinken", completed: true },
  { id: tblItemsIdCounter++, storeId: 3, name: "Brot", completed: true },
  { id: tblItemsIdCounter++, storeId: 4, name: "Brötchen", completed: false },
  { id: tblItemsIdCounter++, storeId: 5, name: "Hackfleisch", completed: false },
  { id: tblItemsIdCounter++, storeId: 4, name: "Salami", completed: false },
  { id: tblItemsIdCounter++, storeId: 5, name: "Pizzateig", completed: true },
  { id: tblItemsIdCounter++, storeId: 2, name: "Mehl", completed: true },
  { id: tblItemsIdCounter++, storeId: 1, name: "Zucker", completed: false },
  { id: tblItemsIdCounter++, storeId: 1, name: "Salz", completed: true },
  { id: tblItemsIdCounter++, storeId: 1, name: "Baguette de Baguette del Parmesane", completed: false },
]);

provide("selectedListId", selectedListId);
provide("lists", tblLists);
provide("stores", tblStores);
provide("items", tblItems);

</script>

<template>
  <header></header>

  <main>

    <div v-if="selectedListId === -1">
      <h1>Einkaufslisten</h1>
      <div class="layout-cards">
        <ShoppingList v-for="list in tblLists" :key="list.id" :name="list.name" @click="selectedListId = list.id" />
      </div>
    </div>

    <div v-else>
      <div class="layout-mid">
        <button class="btn mr-1" @click="selectedListId = -1">&#60;</button>
        <h2>{{ tblLists[selectedListId].name }}</h2>
      </div>

      <h1>Läden</h1>
      <div class="layout-cards">
        <StoreList v-for="store in tblStores.filter(store => store.listId === selectedListId)" :key="store.id"
          :name="store.name" :storeId="store.id" />
      </div>
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
