<template>
  <ChartComp />
  <onlyChart />
</template>

<script>
import ChartComp from "./components/ChartComp.vue";
import onlyChart from "./components/onlyChart.vue";

export default {
  data() {
    return {};
  },
  name: "App",
  components: {
    ChartComp,
    onlyChart,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
flex-direction: column;
align-items: center;
}

#container{
  width: 500px;
  
}
</style>
