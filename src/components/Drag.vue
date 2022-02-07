<template>
  <div class="row row-cols-1 text-center">
    <drag class="card bg-dark text-light p-3 col" :transfer-data="textbox"
      >Text Field</drag
    >
    <drag class="card bg-dark text-light p-3 col" :transfer-data="numberbox"
      >Number Field</drag
    >
    <drag class="card bg-dark text-light p-3 col" :transfer-data="checkbox"
      >Checkbox Field</drag
    >
    <drag class="card bg-dark text-light p-3 col" :transfer-data="radiobox"
      >Radio Field</drag
    >
    <drag class="card bg-dark text-light p-3 col" :transfer-data="datebox"
      >Date Field</drag
    >
    <drag class="card bg-dark text-light p-3 col" :transfer-data="passwordbox"
      >Password Field</drag
    >
    <drag class="card bg-dark text-light p-3 col" :transfer-data="submitbox"
      >Submit Field</drag
    >
  </div>
</template>

<script>
import { Drag } from "vue-drag-drop";
export default {
  name: "drag-area",
  components: {
    Drag,
  },
  data: function () {
    return {
      textbox: {
        types: "text",
        info: "Enter text here....",
      },
      numberbox: {
        types: "number",
        info: "Enter number here....",
      },
      checkbox: {
        types: "checkbox",
        info: "Enter checkbox here....",
      },
      radiobox: {
        types: "radio",
        info: "Enter radio here....",
      },
      datebox: {
        types: "date",
        info: "Enter date here....",
      },
      passwordbox: {
        types: "password",
        info: "Enter password here....",
      },
      submitbox: {
        types: "submit",
        info: "Enter submit here....",
      },
    };
  },
};
</script>

<style scoped>
.box {
  width: 320px;
  padding: 10px;
  border: 5px solid gray;
  margin: 0;
}
.card{
cursor: -webkit-grab; cursor: grab;}
</style>