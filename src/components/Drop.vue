<template>
  <div class="mt-2">
    <drop class="box" @drop="handelDrop">
      <div v-for="d in divs" :key="d.id">
        <input :type="d.data" :placeholder="d.name" />
        <br />
        <br />
      </div>
    </drop>
    <button class="btn btn-success" @click="formCreate">Create Form</button>
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
    };
  },
  methods: {
    handelDrop: function (data, event) {
      var newitem = {
        data: data.types,
        name: data.info,
        id: this.divs.length,
      };
      event;
      this.divs.push(newitem);
      console.log(this.divs);
    },
    check:function(){
        this.$router.push({name:"form"})
    },
    formCreate: function () {
      if (!localStorage.getItem("Formtypes")) {
        localStorage.setItem("Formtypes", JSON.stringify([]));
      }
      const formbuild = JSON.parse(localStorage.getItem("Formtypes"));

      this.divs.map((value) => {
        formbuild.push({"id": value.id,"data":value.data,"name":value.name})
        localStorage.setItem("Formtypes", JSON.stringify(formbuild));
      });
      this.divs=[];
      swal("Nice!", "You Created a form!", "success");
      this.$router.push({name:"form"})
    },
  },
};
</script>

<style scoped>
.box {
  width: 100%;
  height: 540px;
  border: 2px solid rgb(139, 132, 132);
  border-radius: 8px;
  padding: 5px;
}
</style>