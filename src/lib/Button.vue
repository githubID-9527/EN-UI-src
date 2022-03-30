<template>
  <button
    class="en-button"
    :class="classes"
    :disabled="disabled"
    :loading="loading"
  >
    <span v-if="loading" class="en-loadingIndicator"></span>
    <slot />
  </button>
</template>

<script>
import { computed } from "vue";
export default {
  name: "Button",
  props: {
    theme: {
      type: String,
      default: "button",
    },
    size: {
      type: String,
      default: "normal",
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    loading: {
      type: Boolean,
      default: false,
    },
  },
  setup(props) {
    const { theme, size } = props;
    const classes = computed(() => {
      return {
        [`en-theme-${theme}`]: theme,
        [`en-size-${size}`]: size,
      };
    });
    return { classes };
  },
};
</script>

<style lang="scss" >
.en-button {
  box-sizing: border-box;
  white-space: nowrap;
  cursor: pointer;
  background: #fff;
  border: 1px solid #dcdfe6;
  color: #606266;
  text-align: center;
  font-weight: 500;
  padding: 12px 20px;
  font-size: 14px;
  border-radius: 4px;
  margin-left: 10px;
  margin-bottom: 10px;
  &:hover,
  &:focus {
    color: white;
    background-color: lighten(#43d7dd, 10%);
    border-color: lighten(#43d7dd, 10%);
  }
  &[round] {
    border-radius: 20px;
    padding: 12px 23px;
  }
  &.en-theme-primary {
    color: rgba(255, 255, 255, 0.9);
    background-color: rgb(80, 235, 195);
    border-color: rgb(80, 235, 195);
    &:hover,
    &:focus {
      background-color: lighten(rgb(80, 235, 195), 10%);
      border-color: lighten(rgb(80, 235, 195), 10%);
    }
    &[disabled] {
      color: #8c9099;
      background-color: rgba(80, 235, 195, 0.5);
      border-color: rgba(80, 235, 195, 0.5);
    }
  }
  &.en-theme-warning {
    color: rgba(255, 255, 255, 0.9);
    background-color: #ffc75f;
    border-color: #ffc75f;
    &:hover,
    &:focus {
      background-color: lighten(#ffc75f, 10%);
      border-color: lighten(#ffc75f, 10%);
    }
    &[disabled] {
      color: #8c9099;
      background-color: rgba(#ffc75f, 0.5);
      border-color: rgba(#ffc75f, 0.5);
    }
  }
  &.en-theme-danger {
    color: rgba(255, 255, 255, 0.9);
    background-color: #f94646;
    border-color: #f94646;
    &:hover,
    &:focus {
      background-color: lighten(#f94646, 10%);
      border-color: lighten(#f94646, 10%);
    }
    &[disabled] {
      color: #8c9099;
      background-color: rgba(#f94646, 0.5);
      border-color: rgba(#f94646, 0.5);
    }
  }

  &.en-size-big {
    height: 44px;
    line-height: 44px;
    padding: 0 25px;
    font-size: 16px;
  }
  &.en-size-small {
    height: 30px;
    line-height: 30px;
    padding: 0 10px;
    font-size: 12px;
  }
  &.en-size-mini {
    height: 22px;
    line-height: 22px;
    padding: 0 5px;
    font-size: 12px;
  }
  &[disabled] {
    color: #8c9099;
    cursor: not-allowed;
    background-image: none;
    background-color: #fff;
    border-color: #ebeef5;
  }
  > .en-loadingIndicator {
    width: 14px;
    height: 14px;
    display: inline-block;
    margin-right: 8px;
    border-radius: 8px;
    border-color: #8c9099 #8c9099 #8c9099 transparent;
    border-style: dashed;
    border-width: 1px;
    animation: en-rotating 2s infinite linear;
  }
  @keyframes en-rotating {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
  &.en-theme-text {
    border-color: transparent;
    color: rgb(80, 235, 195);
    background: transparent;
    padding-left: 0;
    padding-right: 0;
    margin-right: 5px;
    &[disabled] {
      color: #8c9099;
    }
  }
}
</style>