<template>
  <div id="app">
    <div>
    <h1>Greet</h1>
    <component v-for="(field, index) in schema"
               :key="index"
               :is="field.fieldType"
               v-model="formData[field.name]"
               v-bind="field">

    </component>
    <p>
      Hello {{formData.title}} {{formData.firstName}} {{formData.lastName}}, I hear you are {{formData.age}} years old.
    </p>
  </div>
    <router-view></router-view>
  </div>
</template>

<script>
import NumberInput from "./NumberInput";
import SelectList from "./SelectList";
import TextInput from "./TextInput";

export default {
  name: "FormsDemo",
  components: { NumberInput, SelectList, TextInput },
  data() {
    return {
      formData: {
        firstName: "Evan"
      },
      schema: [
        {
          fieldType: "SelectList",
          name: "title",
          multi: false,
          label: "Title",
          options: ["", "Mr", "Ms", "Mx", "Dr", "Madam", "Lord"]
        },
        {
          fieldType: "TextInput",
          placeholder: "First Name",
          label: "First Name",
          name: "firstName"
        },
        {
          fieldType: "TextInput",
          placeholder: "Last Name",
          label: "Last Name",
          name: "lastName"
        },
        {
          fieldType: "NumberInput",
          placeholder: "Age",
          name: "age",
          label: "Age",
          minValue: 0
        }
      ]
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

ul.nav > li {
  display: inline;
  padding-left: 10px;
}
ul.nav > li::before {
  content: "\2630";
  padding-right: 5px;
}
</style>
