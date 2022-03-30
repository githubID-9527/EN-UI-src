<demo>
    常规用法
</demo>
<template>
  <Button theme="text" @click="toggle">点击打开 dialog</Button>
  <Dialog v-model:visible="x" :ok="f1" :cancel="f2">
    <template v-slot:title>标题</template>
    <template v-slot:content>这是一些提示信息</template>
  </Dialog>
</template>
<script lang="ts">
import { ref } from "vue";
import Button from "../lib/Button.vue";
import Dialog from "../lib/Dialog.vue";
export default {
  name: "DialogDemo",
  components: { Dialog, Button },
  setup() {
    const x = ref(false);
    const toggle = () => {
      x.value = !x.value;
    };
    const f1 = () => {};
    const f2 = () => {};
    return { x, toggle, f1, f2 };
  },
};
</script>
