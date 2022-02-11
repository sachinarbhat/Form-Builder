<template>
  <div class="mt-2 p-2 dropmainbox">
    <div class="row">
      <div class="col-11 a">
        <drop class="box" @drop="handelDrop">
          <div class="row justify-content-start">
            <div class="col-2">
              <p class="mb-3" v-for="l in label" :key="l.id">{{ l.name }}</p>
            </div>
            <div class="col-4">
              <div class="mt-1" v-for="d in divs" :key="d.id">
                <div v-if="d.data == 'textarea'">
                  <textarea :placeholder="d.name"></textarea>
                </div>
                <div v-else>
                  <input class="mb-2" :type="d.data" :placeholder="d.name" />
                </div>
              </div>
            </div>
            <div class="col-5">
              <div class="mt-1" v-for="l in links" :key="l.id">
                <a v-if="l.name != undefined" :href="l.name">Click here</a>
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
      links: [],
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
      var linkname = {
        name: data.linkname,
        id: this.links.length,
      };
      if (linkname.name != undefined) {
        this.links.push(linkname);
      }
      if (newitem.data != undefined) {
        this.divs.push(newitem);
      }
      if (labelitem.name != undefined) {
        this.label.push(labelitem);
      }
      event;
    },
    check: function () {
      this.$router.push({ name: "form" });
    },
    formCreate: function () {
      if (!localStorage.getItem("Fullform")) {
        localStorage.setItem("Fullform", JSON.stringify([]));
      }
      const fullform = JSON.parse(localStorage.getItem("Fullform"));
      if (this.label.length < this.divs.length) {
        let min = this.label.length;
        let max = this.divs.length;
        for (let i = min; i <= max; i++) {
          let labelitem = {
            name: "No_label",
            id: i,
          };
          this.label.push(labelitem);
        }
        console.log(this.label);
      }

      if (this.links.length < this.label.length) {
        let min = this.links.length;
        let max = this.label.length;
        for (let i = min; i <= max; i++) {
          let linkitem = {
            name: "No_link",
            id: i,
          };
          this.links.push(linkitem);
        }
      }
      if (this.links.length < this.divs.length) {
        let min = this.links.length;
        let max = this.divs.length;
        for (let i = min; i <= max; i++) {
          let linkitem = {
            name: "No_link",
            id: i,
          };
          this.links.push(linkitem);
        }
      }

      for (let i = 0; i < this.divs.length; i++) {
        if (this.label[i].name === undefined) {
          console.log("you Got me");
        } else {
          fullform.push({
            id: i,
            inputtype: this.divs[i].data,
            name: this.label[i].name,
            linkname: this.links[i].name,
          });
          localStorage.setItem("Fullform", JSON.stringify(fullform));
        }
      }

      this.label = [];
      this.divs = [];
      this.links=[];
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