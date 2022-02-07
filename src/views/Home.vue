<template>
  <div class="mt-3">
    <h2><i class="fa fa-wpforms"></i> Form Builder</h2>
    <div class="row">
      <div class="col-sm-10">
        <drop></drop>
      </div>
      <div class="col-sm-2">
        <drag></drag>
      </div>
    </div>
  </div>
</template>

<script>
import Drag from "../components/Drag.vue";
import Drop from "../components/Drop.vue";

export default {
  name: "Home",
  components: { Drag, Drop },
};
</script>
<style scoped>
h2 {
  text-align: center;
}
</style>
