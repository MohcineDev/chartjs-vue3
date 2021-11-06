<template>
  <div id="container">
    <canvas id="myChart"></canvas>
  </div>
</template>

<script>
import { Chart, registerables } from "chart.js";
Chart.register(...registerables);
//only chart js
export default {
  data() {
    return {
      countries: [],
      countryandcount: [],
    };
  },
  created() {
    //add register here just in case
  },
  methods: {
    fetchData: async function () {
      const data = await fetch("./chart.json");
      const response = await data.json();

      this.getContries(response);
    },
    getContries: function (truckers) {
      //get truckers country
      truckers.map((item) => this.countries.push(item.location));
      this.getcountryandcount();
    },
    getcountryandcount: function () {
      for (let i = 0; i < this.countries.length; i++) {
        //first time the array is empty
        if (this.countryandcount.length) {
          let countryFound = false; //initialize the variable

          for (let a = 0; a < this.countryandcount.length; a++) {
            //if the country already exist add one to the count
            if (this.countryandcount[a].country == this.countries[i]) {
              countryFound = true;
              this.countryandcount[a].count++;
              break; ///if true break the loop
            }
          }
          if (!countryFound) {
            //if  the country dose not exist add it to the array
            this.countryandcount.push({ country: this.countries[i], count: 1 });
          }
        } else {
          //first time the array is empty
          this.countryandcount.push({ country: this.countries[i], count: 1 });
        }
      }
      this.drawChart();
    },
    drawChart: function () {
      const ctx = document.getElementById("myChart").getContext("2d");
      const myChart = new Chart(ctx, {
        type: "doughnut",
        data: {
          labels: [...this.countryandcount.map((item) => item.country)],
          datasets: [
            {
              label: "# of Votes",
              data: [...this.countryandcount.map((item) => item.count)],
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
  },
  mounted() {
    this.fetchData();
  },
};
</script>


