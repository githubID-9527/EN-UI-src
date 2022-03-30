<template>
  <template v-if="visible">
    <div class="en-dialog-overlay" @click="onClickOverlay"></div>
    <div class="en-dialog-wrapper">
      <div class="en-dialog">
        <header class="en-dialog-header">
          <span class="en-header-title">
              <slot name="title"/>
          </span>
          <button class="en-header-button" @click="close">x</button>
        </header>
        <main class="en-dialog-main">
          <p>
              <slot name="content"/>
          </p>
        </main>
        <footer class="en-dialog-footer">
          <Button @click="cancel">取消</Button>
          <Button theme="primary" @click="ok">确定</Button>
        </footer>
      </div>
    </div>
  </template>
</template>

<script lang="ts">
import Button from "./Button.vue";
export default {
  name: "Dialog",
  components: { Button },
  props: {
    visible: {
      type: Boolean,
      default: false,
    },
    ok: {
      type: Function,
    },
    cancel: {
      type: Function,
    },
  },
  setup(props, context) {
    const close = () => {
      context.emit("update:visible", false);
    };
    const cancel = () => {
      context.emit("cancel");
      close();
    };
    const ok = () => {
      if (props.ok?.() !== false) {
        close();
      }
    };
    return { close, cancel, ok };
  },
};
</script>

<style lang="scss">
.en-dialog-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: fade_out(rgb(122, 122, 122), 0.7);
  z-index: 30;
}
.en-dialog-wrapper {
  position: fixed;
  z-index: 2005;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  overflow: auto;
  margin: 0;
  > .en-dialog {
    position: relative;
    margin: 0 auto 50px;
    background: #fff;
    border-radius: 2px;
    box-shadow: 0 1px 3px rgb(0 0 0 / 30%);
    box-sizing: border-box;
    margin-top: 15vh;
    width: 50%;
    > .en-dialog-header {
      padding: 20px 20px 10px;
      > .en-header-title {
        line-height: 24px;
        font-size: 18px;
        color: #303133;
      }
      > .en-header-button {
        position: absolute;
        top: 20px;
        right: 20px;
        padding: 0;
        background: transparent;
        border: none;
        outline: none;
        cursor: pointer;
        font-size: 16px;
        &:hover {
          color: rgb(80, 235, 195);
        }
      }
    }
    > .en-dialog-main {
      padding: 30px 20px;
      color: #606266;
      font-size: 14px;
      word-break: break-all;
    }
    > .en-dialog-footer {
      display: flex;
      flex-wrap: nowrap;
      justify-content: center;
      padding: 20px 20px;
      box-sizing: border-box;
      > Button {
        margin-right: 10px;
      }
    }
  }
}
</style>