<template>
  <div>
    <div v-for="option in field.options" :key="option.value">
      <label :for="id(field, option)">{{option.label}}</label>
      <input type="radio" :id="id(field, option)" :name="field.key" :value="option.value" @input="$emit('input', $event.target.value)" :placeholder="field.placeholder" :checked="option.value === field.defaultValue" />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    value: String,
    field: Object
  },
  methods: {
    id: function(field, option) {
      return field.key + "." + option.value;
    }
  }
};
</script>