<template>
  <Topnav />
  <Sidebar v-if="width < 900"/>
  <Content />
  <Highlight />
</template>

<script lang="ts">
import {computed, inject, Ref} from "vue"
import Content from "../components/Content.vue";
import Highlight from "../components/Highlight.vue";
import Sidebar from "../components/Sidebar.vue";
import Topnav from "../components/Topnav.vue";
export default {
  name: "Home",
  components: { Topnav, Content, Highlight, Sidebar },
  setup(){
    const width = computed(()=>{
      return inject<Ref<boolean>>("width")
    })
    return { width }
  }
};
</script>

<style lang="scss" scoped>
</style>