<demo>
常规用法
</demo>
<template>
<Tabs v-model:selected="x">
  <Tab title="导航1">内容 1</Tab>
  <Tab title="导航2">内容 2</Tab>
  <Tab title="导航3">内容 3</Tab>
</Tabs>
</template>

<script lang="ts">
import Tabs from '../lib/Tabs.vue'
import Tab from '../lib/Tab.vue'
import {
  ref
} from 'vue'
export default {
  components: {
    Tabs,
    Tab
  },
  setup() {
    const x = ref('导航2')
    return {
      x
    }
  }
}
</script>