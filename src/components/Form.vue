<template>
  <div>
    <button class="btn btn-primary" @click="gotomain">Go back</button>
    <h2><i class="fa fa-file"></i> Your Form</h2>
    <div class="mt-4 box">
          <div  v-for="info in fullform" :key="info.id">
            <label class="form-label" v-if="info.name != 'No_label'">{{ info.name }} </label>
            <br/>
              <input v-if="info.inputtype !='textarea' && info.inputtype !='table'"
              class="mb-3"
              :type="info.inputtype"
              :placeholder="'Enter' + ' ' + info.name + ' ' + 'Here...'"
            /><a v-if="info.linkname!='No_link'" :href="info.linkname"><i class="fa fa-link"></i></a>
            <textarea v-if="info.inputtype=='textarea'" :placeholder="'Enter' + ' ' + info.name + ' ' + 'Here...'"></textarea>
            <table v-if="info.inputtype=='table'" style="width:50%">
            <tr v-for="n in parseInt(info.row)" :key="n">
            <td v-for="n in parseInt(info.col)" :key="n"></td>
            </tr>
            </table>
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
      fullform: [],
    };
  },
  created() {
    if (!localStorage.getItem("Fullform")) {
      localStorage.setItem("Fullform", JSON.stringify([]));
    }
    this.fullform = JSON.parse(localStorage.getItem("Fullform"));
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
      swal(localStorage.getItem("Fullform"));
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
td {
  padding: 15px;
}
table,
td {
  border: 1px solid black;
  border-collapse: collapse;
}
</style>