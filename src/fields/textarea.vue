<template>
  <textarea :value="value" @input="$emit('input', $event.target.value)" :placeholder="field.placeholder" />
</template>

<script>
export default {
  props: {
    value: String,
    field: Object
  }
};
</script>