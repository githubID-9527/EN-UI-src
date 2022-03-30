<template>
  <div class="sidebar" :class="isOpen" v-if="asideVisible">
    <div class="sidebar-inner">
      <ul class="menu-root">
        <li><h3>文档</h3></li>
        <li>
          <router-link to="/doc/intro">介绍</router-link>
        </li>
        <li>
          <router-link to="/doc/install">安装</router-link>
        </li>
        <li>
          <router-link to="/doc/get-start">开始使用</router-link>
        </li>
        <li><h3>组件列表</h3></li>
        <li>
          <router-link to="/doc/switch">Switch 组件</router-link>
        </li>
        <li>
          <router-link to="/doc/button">Button 组件</router-link>
        </li>
        <li>
          <router-link to="/doc/dialog">Dialog 组件</router-link>
        </li>
        <li>
          <router-link to="/doc/tabs">Tabs 组件</router-link>
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { computed, inject, Ref } from "vue";
export default {
  name: "Sidebar",
  setup() {
    const asideVisible = inject<Ref<boolean>>("asideVisible");
    const isOpen = computed(() => {
      return asideVisible ? "open" : "close";
    });
    return { asideVisible, isOpen };
  },
};
</script>

<style lang="scss" scoped>
.sidebar {
  position: fixed;
  z-index: 10;
  top: 61px;
  left: 0;
  bottom: 0;
  overflow-x: hidden;
  overflow-y: auto;
  @media (max-width: 900px) {
    position: fixed;
    background-color: #f9f9f9;
    width: 30%;
    height: 100%;
    top: 40px;
    left: 0;
    box-shadow: 0 0 10px rgb(0 0 0 / 20%);
    animation: fadeInLeft 0.4s cubic-bezier(0.4, 0, 0, 1);
    @keyframes fadeInLeft {
      from {
        opacity: 0;
        transform: translate3d(-100%, 0, 0);
      }
      to {
        opacity: 1;
        transform: translate3d(0, 0, 0);
      }
    }
    @keyframes fadeOutLeft {
      from {
        opacity: 1;
      }

      to {
        opacity: 0;
        transform: translate3d(-100%, 0, 0);
      }
    }
  }

  > .sidebar-inner {
    display: block;
    width: 260px;
    padding: 35px 0px 60px 15px;

    > .menu-root {
      list-style-type: none;
      margin: 0;
      line-height: 1.5em;

      > li {
        display: list-item;
        margin-top: 0.5em;
        > h3 {
          display: block;
          font-size: 1.17em;
          font-weight: 600;
          color: #273849;
          margin-block-start: 1em;
          margin-block-end: 1em;
          margin-inline-start: 0px;
          margin-inline-end: 0px;
        }
        > .router-link-active {
          font-weight: bold;
          color: #7ee7c5;
        }
      }
      // > li.current {
      //   font-weight: 600;
      //   color: #50ebc3;
      // }
    }
  }
}
</style>