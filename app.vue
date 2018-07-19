<template>
  <div>
    <dynamic-form :fields="fields" :layout="layout"></dynamic-form>
  </div>
</template>

<style>
</style>

<script>
import DynamicForm from "./src/form.vue";

export default {
  data: function() {
    return {
      fields: [
        {
          key: "username",
          type: "text",
          name: "username",
          label: "Username",
          placeholder: "Input username",
          defaultValue: "hello"
        },
        {
          key: "password",
          type: "password",
          name: "password",
          label: "Password",
          placeholder: "Input password"
        },
        {
          key: "radio",
          type: "radio",
          name: "Radio",
          label: "Radio",
          placeholder: "chooose the radio",
          defaultValue: "radio1",
          options: [
            {
              label: "radio 1",
              value: "radio1"
            },
            {
              label: "radio 2",
              value: "radio2"
            }
          ]
        }
      ],
      layout: [
        {
          type: "row",
          children: [
            {
              type: "col",
              span: 4,
              fieldKey: "username"
            },
            {
              type: "col",
              span: 4,
              fieldKey: "password"
            }
          ]
        },
        {
          type: "row",
          children: [
            {
              type: "col",
              span: 4,
              fieldKey: "username"
            },
            {
              type: "col",
              span: 4,
              fieldKey: "radio"
            }
          ]
        },
        {
          type: "row",
          children: [
            {
              type: "col",
              span: 4,
              fieldKey: "password"
            }
          ]
        }
      ]
    };
  },
  components: {
    DynamicForm
  }
};
</script>