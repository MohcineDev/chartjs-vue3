<template>
  <div class="small">

  <canvas id="myChart" width="100%"></canvas>
  </div>
</template>

<script>
import { Chart,  registerables } from "chart.js";
Chart.register(...registerables);

export default {
  methods: {
  
  },
  mounted() {
     const ctx = document.getElementById("myChart").getContext("2d");
      const myChart = new Chart(ctx, {
        type: "doughnut",
        data: {
          labels: ["Red", "Blue", "Yellow", "Green", "Purple"],
          datasets: [
            {
              label: "# of Votes",
              data: [12, 19, 3, 5, 2],
              backgroundColor: [
                "rgb(255, 99, 132)",
                "rgb(255, 159, 64)",
                "rgb(255, 205, 86)",
                "rgb(75, 192, 192)",
                "rgb(54, 162, 235)",
              ],
              borderColor: "#fff",
              borderWidth: 1,
            },
          ],
        },
        options: {},
      });
  },
};
</script>

<style>
#myChart{
  
}

</style>