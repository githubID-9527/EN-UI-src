<template>
  <div>
    <Topnav />
    <div class="layout">
      <Sidebar/>
      <div class="content">
        <router-view />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Topnav from "../components/Topnav.vue";
import Sidebar from "../components/Sidebar.vue";
import SwitchDemo from "../components/SwitchDemo.vue";
import { inject, Ref } from "vue";
export default {
  name: "Doc",
  components: { Topnav, Sidebar, SwitchDemo },
  setup() {
    const asideVisible = inject<Ref<boolean>>("asideVisible"); // get
    return { asideVisible };
  },
};
</script>

<style lang="scss" scoped>
.layout {
  position: relative;
  z-index: 1;
  padding: 0 60px 30px;
  overflow-x: hidden;
  > .content {
    position: relative;
    padding: 35px 0;
    max-width: 700px;
    margin: 50px auto;
    padding-left: 0px;
  }
}
</style>