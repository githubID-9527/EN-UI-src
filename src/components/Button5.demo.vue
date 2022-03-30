<demo>
按钮尺寸
</demo>
<template>
  <div>
    <Button theme="primary" size="big">大型按钮</Button>
    <Button theme="primary">主要按钮</Button>
    <Button theme="primary" size="small">小型按钮</Button>
    <Button theme="primary" size="mini">迷你按钮</Button>
  </div>
</template>
<script lang="ts">
import Button from "../lib/Button.vue";
export default {
  components: {
    Button
  }
}
</script>