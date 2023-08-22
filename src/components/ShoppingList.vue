<script setup lang="ts">
import { ref, inject } from "vue";

const shoppingLists = inject("lists");

</script>

<template>
  <div>
    <h1>Einkaufsliste [name]</h1>
  </div>
</template>

<style lang="scss" scoped></style>