<template>
  <div class="home__content">
    <agile :options="agileOptions" ref="carousel">
      <div class="slide" v-for="n in 8" :key="n">
        <h3>Slide {{ n }}</h3>
      </div>
    </agile>
  </div>
</template>

<script>
import { VueAgile } from "vue-agile";

export default {
  components: {
    agile: VueAgile
  },
  data() {
    return {
      agileOptions: {
        navButtons: false,
        timing: "ease-in-out",
      },
    };
  },
};
</script>

<style lang="scss" scoped>
.home__content {
  width: 100%;
  height: 100%;
  overflow: hidden;

  span {
    width: 100%;
    height: 100%;
    background: red;
  }
}
</style>
