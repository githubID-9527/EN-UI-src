 <demo>
常规使用
</demo>
<template>
    <Button>默认按钮</Button>
    <Button theme="primary">主要按钮</Button>
    <Button theme="warning">警告按钮</Button>
    <Button theme="danger">危险按钮</Button>
</template>

<script lang="ts">
import Button from "../lib/Button.vue";
export default {
  name: "ButtonDemo",
  components: { Button },
};
</script>