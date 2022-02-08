<template>
  <div>
    <button class="btn btn-primary" @click="gotomain">Go back</button>
    <h2><i class="fa fa-file"></i> Your Form</h2>
    <div class="mt-4 box">
      <div class="row justify-content-start">
        <div class="col-1">
          <p class="mb-3" v-for="l in formlabel" :key="l.id">
            {{ l.labelname }}
          </p>
        </div>
        <div class="col-1">
          <div class="mt-1" v-for="(info, index) in forminfo" :key="index">
            <input class="mb-2" :type="info.data" :placeholder="info.name" />
          </div>
        </div>
      </div>
    </div>
    <button @click="jsonwatch" class="btn btn-outline-info">JSON Watch</button>
  </div>
</template>

<script>
import swal from "sweetalert";
export default {
  name: "form",
  data() {
    return {
      forminfo: [],
      formlabel: [],
    };
  },
  created() {
    if (!localStorage.getItem("Formtypes")) {
      localStorage.setItem("Formtypes", JSON.stringify([]));
    }
    this.forminfo = JSON.parse(localStorage.getItem("Formtypes"));

    if (!localStorage.getItem("Labeltypes")) {
      localStorage.setItem("Labeltypes", JSON.stringify([]));
    }
    this.formlabel = JSON.parse(localStorage.getItem("Labeltypes"));
  },
  methods: {
    gotomain: function () {
      swal({
        title: "Are you sure?",
        text: "Once you go back This form will be cleared",
        icon: "warning",
        buttons: true,
        dangerMode: true,
      }).then((willDelete) => {
        if (willDelete) {
          swal("You can create new form now", {
            icon: "success",
          });
          localStorage.clear();
          this.$router.push({ name: "Home" });
        } else {
          swal("Your Form is Safe....");
        }
      });
    },
    jsonwatch: function () {
      alert(localStorage.getItem("Formtypes"));
    },
  },
};
</script>

<style scoped>
.box {
  width: 100%;
  height: 700px;
  border: 2px solid rgb(139, 132, 132);
  border-radius: 8px;
  padding: 5px;
}
h2 {
  text-align: center;
}
</style>