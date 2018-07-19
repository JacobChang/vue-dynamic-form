<style>
</style>

<template>
  <div class="dynamic_form__field">
    <label :for="field.key">{{field.label}}</label>
    <text-input v-if="field.type === 'text'" :field="field" :value="value" @input="onInput" />
    <password-input v-else-if="field.type === 'password'" :field="field" :value="value" @input="onInput" />
    <radio-input v-else-if="field.type === 'radio'" :field="field" :value="value" @input="onInput" />
    <checkbox-input v-else-if="field.type === 'checkbox'" :field="field" :value="value" @input="onInput" />
    <textarea-input v-else-if="field.type === 'textarea'" :field="field" :value="value" @input="onInput" />
  </div>
</template>

<script>
import TextInput from "./fields/text.vue";
import PasswordInput from "./fields/password.vue";
import CheckboxInput from "./fields/checkbox.vue";
import RadioInput from "./fields/radio.vue";
import TextareaInput from "./fields/textarea.vue";

export default {
  props: {
    fieldKey: String,
    fields: Array,
    value: String
  },
  data: function() {
    let field = this.fields.find(field => {
      return field.key === this.fieldKey;
    });

    return {
      field
    };
  },
  methods: {
    onInput: function(value) {
      this.$emit("input", value);
    }
  },
  components: {
    TextInput,
    PasswordInput,
    CheckboxInput,
    RadioInput,
    TextareaInput
  }
};
</script>