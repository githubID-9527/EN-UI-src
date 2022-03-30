<template>
  <h3>{{component.__sourceCodeTitle}}</h3>
  <div class="demo-block">
    <div class="source">
      <component :is="component" />
    </div>
    <div class="meta">
      <div class="code" v-if="codeVisible">
        <pre class="language-html" v-html="html"></pre>
      </div>
    </div>
    <div class="demo-block-control" @click="codeVisible = !codeVisible">
      <span v-if="!codeVisible">显示代码</span>
      <span v-if="codeVisible">隐藏代码</span>
    </div>
  </div>
</template>
<script lang="ts">
import  "prismjs"
import "prismjs/themes/prism.css"
import { computed, ref } from 'vue'
const Prism = (window as any).Prism
export default{
    name: "Demo",
    props: {
        component: Object,
    },
    setup(props){
        const html = computed(()=>{
            return Prism.highlight(props.component.__sourceCode, Prism.languages.html, 'html')
        })
        const codeVisible = ref(false)
        return {Prism, html, codeVisible}
    }
}
</script>

<style lang="scss">
h2,
h3 {
  display: block;
  margin-block-start: 1em;
  margin-block-end: 1em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  color: #1f2f3d;
  font-weight: 400;
}
h2 {
  font-size: 28px;
  margin: 0;
}
h3 {
  font-size: 22px;
  margin: 55px 0 20px;
}
.demo-block {
  border: 1px solid #ebebeb;
  border-radius: 3px;
  margin-bottom: 24px;
  > .source {
    padding: 24px;
  }
  > .meta {
    background-color: #fafafa;
    border-top: 1px solid #eaeefb;
    overflow: hidden;
    // height: 0;
    transition: height 0.2s;
    > .code {
      padding: 20px;
      box-sizing: border-box;
      border: 1px px solid #ebebeb;
      border-radius: 3px;
      font-size: 14px;
      line-height: 22px;
      color: #666;
      word-break: break-word;
      margin: 10px;
      background-color: #fff;
    }
  }
  > .demo-block-control {
    border-top: 1px solid #eaeefb;
    height: 44px;
    box-sizing: border-box;
    background-color: #fff;
    border-bottom-left-radius: 4px;
    border-bottom-right-radius: 4px;
    text-align: center;
    margin-top: -1px;
    color: #d3dce6;
    cursor: pointer;
    position: relative;
    translate: all 0.4s ease-in;
    &:hover {
      color: #7ee5c7;
      box-shadow: 0 0 8px 0 rgb(232 237 250 / 60%),
        0 2px 4px 0 rgb(232 237 250 / 50%);
    }
    > span {
      display: inline-block;
      position: absolute;
      font-size: 14px;
      line-height: 44px;
      transform: translateX(-30px);
    }
  }
}
</style>