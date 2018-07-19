<style>
.dynamic_form__row {
  display: flex;
}
</style>

<template>
  <div class="dynamic_form__row">
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    name: String
  }
};
</script>