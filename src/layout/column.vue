<style>
.dynamic_form__column {
  flex: 1;
}
</style>

<template>
  <div :style="{flex: span}" class="dynamic_form__column">
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    span: Number
  }
};
</script>