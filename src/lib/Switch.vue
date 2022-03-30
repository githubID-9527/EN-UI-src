<template>
  <button class="en-switch" @click="toggle" :class="{ 'en-checked': value }">
    <span></span>
  </button>
</template>
<script lang="ts">
import { computed } from "vue";
export default {
  props: {
    value: Boolean,
  },
  setup(props, context) {
    const isOn = computed(()=>{
      return props.value
    })
    const toggle = () => {
      context.emit("update:value", !props.value);
    };
    return { toggle, isOn };
  },
};
</script>

<style lang="scss" >
$h: 22px;
$h2: $h - 4px;
.en-switch {
  height: 22px;
  width: 50px;
  border: none;
  background: #d2d2d2;
  border-radius: $h/2;
  position: relative;
  > span {
    position: absolute;
    top: 2px;
    left: 2px;
    height: $h2;
    width: $h2;
    background: white;
    border-radius: $h2 / 2;
    transition: all 250ms;
  }
  &.en-checked {
    background: #7ee5c7;
    > span {
      left: calc(100% - #{$h2} - 2px);
    }
  }
  &:focus {
    outline: none;
  }
  &:active {
    > span {
      width: $h2 + 4px;
    }
  }
  &.en-checked:active {
    > span {
      width: $h2 + 4px;
      margin-left: -4px;
    }
  }
}
</style>