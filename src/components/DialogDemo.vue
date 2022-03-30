<template>
  <h2>Dialog 对话框</h2>
  <Demo :component="Dialog1Demo" />
</template>
<script lang="ts">
import Demo from "./Demo.vue";
import Dialog1Demo from "./Dialog.demo.vue";
export default {
  name: "DialogDemo",
  components: { Demo },
  setup() {
    return { Dialog1Demo };
  },
};
</script>