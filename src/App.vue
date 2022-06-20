<template>
  <div id="app">
    <HeaderLastFm />
    <BandList />
  </div>
</template>

<script>
import HeaderLastFm from "./components/HeaderLastFm.vue";
import BandList from "./components/BandList.vue";

export default {
  name: "App",
  components: {
    HeaderLastFm,
    BandList,
  },
  data() {
    return {
      teste: "Hello World",
    };
  },
};
</script>

<style>
@import "./assets/css/style.css";
</style>
