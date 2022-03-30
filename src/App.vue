<template>
  <router-view />
</template>

<script lang="ts">
import { ref, provide } from "vue";
import { router } from "./router.ts";

export default {
  name: "App",
  setup() {
    const width = document.documentElement.clientWidth;
    const asideVisible = ref(width <= 900 ? false : true);
    provide("asideVisible", asideVisible);
    provide("width", width);
    router.afterEach(() => {
      if (width <= 900) {
        asideVisible.value = false;
      }
    });
  },
};
</script>
