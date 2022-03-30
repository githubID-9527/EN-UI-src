<template>
  <div id="mobile-bar">
    <div class="menu-button" @click="toggleMenu"></div>
    <router-link to="/" class="logo"></router-link>
  </div>
  <header>
    <router-link to="/" id="logo">
      <span>EN UI</span>
    </router-link>
    <ul id="nav">
      <li>
        <router-link to="/doc">文档</router-link>
      </li>
    </ul>
  </header>
</template>

<script lang="ts">
import { inject, Ref } from "vue";
export default {
  setup() {
    const asideVisible = inject<Ref<boolean>>("asideVisible");
    const toggleMenu = () => {
      asideVisible.value = !asideVisible.value;
    };
    return {
      toggleMenu,
    };
  },
};
</script>

<style lang="scss" scoped>
header {
  background-color: #fff;
  padding: 10px 30px 10px 60px;
  position: relative;
  z-index: 2;
  display: flex;
  justify-content: space-between;
  box-sizing: border-box;
  @media screen and (max-width: 900px) {
    display: none;
  }
  > #logo {
    display: inline-block;
    font-size: 1.5em;
    line-height: 40px;
    color: #273849;
    font-family: "Dosis", "Source Sans Pro", "Helvetica Neue", Arial, sans-serif;
    font-weight: 500;
    > span {
      font-size: 1.2em;
    }
  }

  > #nav {
    list-style-type: none;
    margin: 0;
    padding: 0;
    line-height: 40px;
    > li {
      display: inline-block;
      position: relative;
      margin: 0 0.6em;
    }
  }
}
#mobile-bar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 40px;
  background-color: #fff;
  z-index: 20;
  display: none;
  box-shadow: 0 0 2px rgb(0 0 0 / 25%);
  pointer-events: none;
  @media screen and (max-width: 900px) {
    display: block;
  }
  > .menu-button {
    position: absolute;
    width: 24px;
    height: 24px;
    top: 8px;
    left: 12px;
    background: url(../assets/menu.png) center center no-repeat;
    background-size: 24px;
    pointer-events: auto;
  }
  > .logo {
    position: absolute;
    width: 30px;
    height: 30px;
    background: url(../assets/logo.png) center center no-repeat;
    top: 5px;
    left: 50%;
    margin-left: -17px;
    background-size: 30px;
    pointer-events: auto;
  }
}
</style>