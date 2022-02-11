<template>
  <div class="mt-2 list-group rounded">
    <div class="text-warning list-group-item" data-bs-toggle="collapse" data-bs-target="#collapseExample" aria-expanded="false" aria-controls="collapseExample">General</div>
    <div class="collapse" id="collapseExample">
          <input v-model="msg.labelname" placeholder="Enter the label" />
          <drag class="list-group-item" :transfer-data="msg">Label</drag>
          <drag class="list-group-item" :transfer-data="textbox">Textbox</drag>
          <drag class="list-group-item" :transfer-data="textareabox">Textarea</drag>
          <drag class="list-group-item" :transfer-data="radiobox">Radio Button</drag>
          <drag class="list-group-item" :transfer-data="checkbox">Checkbox</drag>
          <drag class="list-group-item" :transfer-data="submitbox">Button</drag>
          <input v-model="msg2.linkname" placeholder="Enter the URL to Link" />
          <drag class="list-group-item" :transfer-data="msg2">Link Button</drag>
          <drag class="list-group-item" :transfer-data="datebox">Datepicker</drag>
    </div>
    <div class="text-warning list-group-item" data-bs-toggle="collapse" data-bs-target="#collapseExample2" aria-expanded="false" aria-controls="collapseExample2">Advanced</div>
        <div class="collapse" id="collapseExample2">
        <drag class="list-group-item" :transfer-data="filebox">File Upload</drag>
        <drag class="list-group-item" :transfer-data="urlbox">URL</drag>
    </div>
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
      msg: {
        labelname: "",
      },
      msg2: {
        linkname: "",
      },
      textareabox: {
        types: "textarea",
        info: "Enter text area here....",
      },
      textbox: {
        types: "text",
        info: "Enter text here....",
      },
      filebox: {
        types: "file",
        info: "Choose your file",
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
      urlbox: {
        types: "url",
        info: "Enter URL here....",
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
.list-group {
  cursor: -webkit-grab;
  cursor: grab;
}
.list-group-item {
  background-color: whitesmoke;
}
</style>