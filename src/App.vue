<script setup lang="ts">
import Menu from "./components/Menu.vue";
import { RouterView } from "vue-router";
</script>

<template>
  <header>
    <Menu></Menu>
  </header>

  <RouterView />
</template>