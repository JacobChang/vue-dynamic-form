<style>
.dynamic_form {
  flex: 1;
}
</style>

<template>
  <div class="dynamic_form">
    <slot name="header"></slot>
    <form @submit="onSubmit">
      <template v-for="(container, index) in layout">
        <row v-if="container.type === 'row'" :key="index">
          <template v-for="(column, index) in container.children">
            <column :span="column.span" :key="index">
              <field :fieldKey="column.fieldKey" :fields="fields" v-model="models[column.fieldKey]" />
            </column>
          </template>
        </row>
      </template>
    </form>
    <slot name="footer"></slot>
  </div>
</template>

<script>
import Row from "./layout/row";
import Column from "./layout/column";
import Field from "./field";

export default {
  props: {
    fields: Array,
    layout: Array
  },
  data: function() {
    let models = {};
    for (let container of this.layout) {
      switch (container.type) {
        case "row":
          for (let column of container.children) {
            let field = this.fields.find(
              field => field.key === column.fieldKey
            );
            if (field) {
              switch (field.type) {
                case "text":
                  models[field.key] = field.defaultValue || "";
                  break;
                case "password":
                  models[field.key] = "";
                  break;
              }
            }
          }
          break;
        default:
          break;
      }
    }
    console.log(models);
    return {
      models
    };
  },
  methods: {
    onSubmit: function() {
      console.log(this);
    }
  },
  components: {
    Row,
    Column,
    Field
  }
};
</script>
