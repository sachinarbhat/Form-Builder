<template>
  <div class="mt-2 list-group rounded">
  <div class="text-warning list-group-item">General</div>
    <drag class="list-group-item" :transfer-data="textbox"
      >Text Field</drag
    >
    <drag class="list-group-item" :transfer-data="numberbox"
      >Number Field</drag
    >
    <drag class="list-group-item" :transfer-data="checkbox"
      >Checkbox Field</drag
    >
    <drag class="list-group-item" :transfer-data="radiobox"
      >Radio Field</drag
    >
    <drag class="list-group-item" :transfer-data="datebox"
      >Date Field</drag
    >
    <drag class="list-group-item" :transfer-data="passwordbox"
      >Password Field</drag
    >
    <drag class="list-group-item" :transfer-data="submitbox"
      >Submit Field</drag
    >
    <input v-model="msg.labelname" placeholder="Enter the label"/>
    <drag class="list-group-item" :transfer-data="msg">Drag Label</drag>
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
      msg:{
        labelname:""
      },
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
.list-group{
cursor: -webkit-grab; cursor: grab;
}
.list-group-item{
  
background-color: whitesmoke;
}
</style>