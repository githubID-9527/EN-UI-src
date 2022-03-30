<template>
  <h2>Switch 开关</h2>
  <Demo :component="Switch1Demo" />
  <Demo :component="Switch2Demo" />
</template>

<script lang="ts">
import Switch1Demo from "../components/Switch1.demo.vue";
import Switch2Demo from "../components/Switch2.demo.vue";
import Demo from "../components/Demo.vue";

const Prism = (window as any).Prism;
export default {
  name: "SwitchDemo",
  components: { Demo },
  setup() {
    return {
      Switch1Demo,
      Switch2Demo,
    };
  },
};
</script>