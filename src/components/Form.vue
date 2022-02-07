<template>
  <div class="bg-dark text-light">
    <button class="btn btn-primary" @click="gotomain">Go back</button>
    <h2><i class="fa fa-file"></i> Your Form</h2>
    <div class="mt-4 box">
      <div v-for="(info, index) in forminfo" :key="index">
        <input :type="info.data" :placeholder="info.name" />
        <br />
        <br />
      </div>
    </div>
  </div>
</template>

<script>
import swal from "sweetalert";
export default {
  name: "form",
  data() {
    return {
      forminfo: [],
    };
  },
  created() {
    if (!localStorage.getItem("Formtypes")) {
      localStorage.setItem("Formtypes", JSON.stringify([]));
    }
    this.forminfo = JSON.parse(localStorage.getItem("Formtypes"));
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