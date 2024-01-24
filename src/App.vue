<script setup lang="ts">
import Menu from "./components/Menu.vue";
import { RouterView } from "vue-router";
</script>

<template>
  <Menu>
    <RouterView />
  </Menu>
</template>