<template>
  <main id="hero">
    <div class="inner">
      <div class="left">
        <img src="../assets/logo.png" alt="EN logo" />
      </div>
      <div class="right">
        <h2 class="EN">EN UI</h2>
        <h1>一个实用的 UI</h1>
        <p>
          <a href="https://github.com" target="_blank">GITHUB</a>
          <router-link to="/doc">开始</router-link>
        </p>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
export default {
  name: "Content",
};
</script>

<style lang="scss" scoped>
#hero {
  padding: 40px 40px 30px;
  background-color: #fff;
  > .inner {
    max-width: 1260px;
    margin: 0 auto;
    > .left {
      display: inline-block;
      vertical-align: top;
      width: 39%;
      @media screen and (max-width: 900px) {
        text-align: center;
        width: 100%;
      }
      > img {
        width: 215px;
        height: 215px;
        float: right;
        margin-right: 60px;
        @media screen and (max-width: 900px) {
          float: none;
          margin: 30px 0 15px;
          width: 140px;
          height: 140px;
        }
      }
    }
    > .right {
      display: inline-block;
      vertical-align: top;
      width: 61%;
      @media screen and (max-width: 900px) {
        text-align: center;
        width: 100%;
      }
      > h2 {
        font-family: "Dosis", "Source Sans Pro", "Helvetica Neue", Arial,
          sans-serif;
        font-weight: 500;
        font-size: 2.4em;
        color: #273849;
        margin: 0 0 10px;
        display: none;
        @media screen and (max-width: 900px) {
          display: block;
        }
      }
      > h1 {
        font-weight: 300;
        margin: 30px;
        font-size: 3.2em;
        color: #273849;
        @media screen and (max-width: 900px) {
          font-size: 2em;
        }
      }
      > p a {
        padding: 0.75em 2em;
        border-radius: 2em;
        display: inline-block;
        box-sizing: border-box;
        border: 1px solid #50ebc3;
        background-color: #fff;
        color: #50ebc3;
        margin: 1em 30px;
        font-size: 1.05em;
        font-weight: 600;
        letter-spacing: 0.1em;
        min-width: 8em;
        text-align: center;
        margin-right: 1%;
      }
    }
  }
}
</style>