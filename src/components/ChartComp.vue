<template>
  <div class="small">
    <DoughnutChart :chartData="testData" />
  </div>
</template> 
<script>
import { DoughnutChart } from "vue-chart-3";

import { Chart, registerables } from "chart.js";
Chart.register(...registerables);

export default {
  components: { DoughnutChart },
  setup() {
    const testData = {
      labels: ["United States", "France", "Morocco", "Italy"],
      colors: "red",
      datasets: [
        {
          label: "my data",
          data: [30, 40, 60, 70, 5],
          backgroundColor: [
            "rgb(255, 99, 132)",
            "rgb(255, 159, 64)",
            "rgb(255, 205, 86)",
            "rgb(75, 192, 192)",
            "rgb(54, 162, 235)",
          ],
          borderColor: "#fff",
          hoverOffset: 4,
        },
      ],
    };

    return { testData };
  },
};
</script>

<style>
.small {
    max-width: 500px;
    margin:auto;
  }
</style>