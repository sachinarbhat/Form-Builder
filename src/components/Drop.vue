<template>
  <div class="mt-2 p-2 dropmainbox">
    <div class="row">
      <div class="col-11 a">
        <drop class="box" @drop="handelDrop">
          <div class="row justify-content-start">
            <div class="col-1">
              <p class="mb-3" v-for="l in label" :key="l.id">{{ l.name }}</p>
            </div>
            <div class="col-1">
              <div class="mt-1" v-for="d in divs" :key="d.id">
                <input class="mb-2" :type="d.data" :placeholder="d.name" />
              </div>
            </div>
          </div>
        </drop>
      </div>
      <button class="btn btn-outline-primary b" @click="formCreate">
        Save
      </button>
    </div>
  </div>
</template>

<script>
import { Drop } from "vue-drag-drop";
import swal from "sweetalert";
export default {
  name: "drop-area",
  components: {
    Drop,
  },
  data: function () {
    return {
      divs: [],
      label: [],
    };
  },
  methods: {
    handelDrop: function (data, event) {
      var newitem = {
        data: data.types,
        name: data.info,
        id: this.divs.length,
      };
      var labelitem = {
        name: data.labelname,
        id: this.label.length,
      };
      if (newitem.data != undefined) {
        this.divs.push(newitem);
      }
      if (labelitem.name != undefined) {
        this.label.push(labelitem);
      }
      event;
      console.log(this.label);
    },
    check: function () {
      this.$router.push({ name: "form" });
    },
    formCreate: function () {
      if (!localStorage.getItem("Formtypes")) {
        localStorage.setItem("Formtypes", JSON.stringify([]));
      }
      const formbuild = JSON.parse(localStorage.getItem("Formtypes"));

      this.divs.map((value) => {
        formbuild.push({ id: value.id, data: value.data, name: value.name });
        localStorage.setItem("Formtypes", JSON.stringify(formbuild));
      });

      if (!localStorage.getItem("Labeltypes")) {
        localStorage.setItem("Labeltypes", JSON.stringify([]));
      }
      const labels = JSON.parse(localStorage.getItem("Labeltypes"));

      this.label.map((value) => {
        labels.push({ id: value.id, labelname: value.name });
        localStorage.setItem("Labeltypes", JSON.stringify(labels));
      });
      this.label=[];
      this.divs = [];
      swal("Nice!", "You Created a form!", "success");
      this.$router.push({ name: "form" });
    },
  },
};
</script>

<style scoped>
.box {
  width: 100%;
  height: 510px;
  background-color: whitesmoke;

  padding: 5px;
}
.dropmainbox {
  border: 2px dashed rgb(139, 132, 132);
  background-color: rgb(229, 247, 250);
  border-radius: 8px;
}
.a {
  border-right-style: dashed;
  border-color: rgb(139, 132, 132);
  border-width: 2px;
}
.b {
  position: absolute;
  bottom: 0px;
  width: 100px;
}
</style>