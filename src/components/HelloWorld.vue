<template>
  <div>
    <p>Hello World</p>
    <canvas id="myChart" width="200" height="200"></canvas>
    <canvas id="barChart" width="200" height="200"></canvas>
    <canvas id="bubbleChart" width="200" height="200"></canvas>
    <canvas id="doughnutChart" width="200" height="200"></canvas>
    <canvas id="lineChart" width="200" height="200"></canvas>
    <canvas id="mixedChart" width="200" height="200"></canvas>
    <canvas id="polarChart" width="200" height="200"></canvas>
    <canvas id="radarChart" width="200" height="200"></canvas>
    <canvas id="scatterChart" width="200" height="200"></canvas>

  </div>
</template>

<script>
import Chart from "chart.js/auto";
// const labels = Utils.months({count: 7});
const data = {
  labels: [1, 2, 3, 4, 5, 6, 7],

  datasets: [
    {
      label: "My First Dataset",
      data: [65, 59, 80, 81, 56, 55, 40],
      backgroundColor: [
        "rgba(255, 99, 132, 0.2)",
        "rgba(255, 159, 64, 0.2)",
        "rgba(255, 205, 86, 0.2)",
        "rgba(75, 192, 192, 0.2)",
        "rgba(54, 162, 235, 0.2)",
        "rgba(153, 102, 255, 0.2)",
        "rgba(201, 203, 207, 0.2)",
      ],
      borderColor: [
        "rgb(255, 99, 132)",
        "rgb(255, 159, 64)",
        "rgb(255, 205, 86)",
        "rgb(75, 192, 192)",
        "rgb(54, 162, 235)",
        "rgb(153, 102, 255)",
        "rgb(201, 203, 207)",
      ],
      borderWidth: 1,
    },
  ],
};
const bubbleData = {
  datasets: [
    {
      label: "First Dataset",
      data: [
        {
          x: 20,
          y: 30,
          r: 15,
        },
        {
          x: 40,
          y: 10,
          r: 10,
        },
      ],
      backgroundColor: "rgb(255, 99, 132)",
    },
  ],
};
const doughnutData = {
  labels: ["Red", "Blue", "Yellow"],
  datasets: [
    {
      label: "My First Dataset",
      data: [300, 50, 100],
      backgroundColor: [
        "rgb(255, 99, 132)",
        "rgb(54, 162, 235)",
        "rgb(255, 205, 86)",
      ],
      hoverOffset: 4,
    },
  ],
};
const lineData = {
  labels: [1, 2, 3, 4, 5, 6, 7],
  datasets: [
    {
      label: "My First Dataset",
      data: [65, 59, 80, 81, 56, 55, 40],
      fill: false,
      borderColor: "rgb(75, 192, 192)",
      tension: 0.1,
    },
  ],
};
const polarData = {
  labels: ["Red", "Green", "Yellow", "Grey", "Blue"],
  datasets: [
    {
      label: "My First Dataset",
      data: [11, 16, 7, 3, 14],
      backgroundColor: [
        "rgb(255, 99, 132)",
        "rgb(75, 192, 192)",
        "rgb(255, 205, 86)",
        "rgb(201, 203, 207)",
        "rgb(54, 162, 235)",
      ],
    },
  ],
};

const radarData = {
  labels: [
    "Eating",
    "Drinking",
    "Sleeping",
    "Designing",
    "Coding",
    "Cycling",
    "Running",
  ],
  datasets:[{    label: 'My First Dataset',
    data: [65, 59, 90, 81, 56, 55, 40],
    fill: true,
    backgroundColor: 'rgba(255, 99, 132, 0.2)',
    borderColor: 'rgb(255, 99, 132)',
    pointBackgroundColor: 'rgb(255, 99, 132)',
    pointBorderColor: '#fff',
    pointHoverBackgroundColor: '#fff',
    pointHoverBorderColor: 'rgb(255, 99, 132)'
},
{
    label: 'My Second Dataset',
    data: [28, 48, 40, 19, 96, 27, 100],
    fill: true,
    backgroundColor: 'rgba(54, 162, 235, 0.2)',
    borderColor: 'rgb(54, 162, 235)',
    pointBackgroundColor: 'rgb(54, 162, 235)',
    pointBorderColor: '#fff',
    pointHoverBackgroundColor: '#fff',
    pointHoverBorderColor: 'rgb(54, 162, 235)'
  }]
};
const scatterData ={
  datasets:[{
    label:"Scatter Dataset",
  data: [{
      x: -10,
      y: 0
    }, {
      x: 0,
      y: 10
    }, {
      x: 10,
      y: 5
    }, {
      x: 0.5,
      y: 5.5
    }],
    backgroundColor: 'rgb(255, 99, 132)'
  }]
}
const plugin = {
  id: 'custom_canvas_background_color',
  beforeDraw: (chart) => {
    const ctx = chart.canvas.getContext('2d');
    ctx.save();
    ctx.globalCompositeOperation = 'destination-over';
    ctx.fillStyle = 'lightGreen';
    ctx.fillRect(0, 0, chart.width, chart.height);
    ctx.restore();
  }
};
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  mounted() {
    const ctx = document.getElementById("myChart");
    const myChart = new Chart(ctx, {
      type: "bar",
      data: {
        labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
        datasets: [
          {
            label: "# of Votes",
            data: [12, 19, 3, 5, 2, 3],
            backgroundColor: [
              "rgba(255, 99, 132, 0.2)",
              "rgba(54, 162, 235, 0.2)",
              "rgba(255, 206, 86, 0.2)",
              "rgba(75, 192, 192, 0.2)",
              "rgba(153, 102, 255, 0.2)",
              "rgba(255, 159, 64, 0.2)",
            ],
            borderColor: [
              "rgba(255, 99, 132, 1)",
              "rgba(54, 162, 235, 1)",
              "rgba(255, 206, 86, 1)",
              "rgba(75, 192, 192, 1)",
              "rgba(153, 102, 255, 1)",
              "rgba(255, 159, 64, 1)",
            ],
            borderWidth: 1,
          },
        ],
      },
      options: {
        scales: {
          y: {
            beginAtZero: true,
          },
          x:{
            min:"March",
            grid:{
              borderColor:'red',
              tickColor:'gray'
            }
          }
        },
      },
    });

    const ctx1 = document.getElementById("barChart");
    const barChart = new Chart(ctx1, {
      type: "bar",
      data: data,
      options: {
        scales: {
          y: {
            beginAtZero: true,
          },
        },
      },
    });

    const ctx2 = document.getElementById("bubbleChart");

    const bubbleChart = new Chart(ctx2, {
      type: "bubble",
      data: bubbleData,
      options: "",
    });

    const ctx3 = document.getElementById("doughnutChart");

    const doughnutChart = new Chart(ctx3, {
      type: "doughnut",
      data: doughnutData,
      plugins:[plugin]
    });

    const ctx4 = document.getElementById("lineChart");

    const lineChart = new Chart(ctx4, {
      type: "line",
      data: lineData,
      options:{
        animations:{
          tension:{
             duration: 2000,
        easing: 'easeInQuad',
        from: 1,
        to: 0,
        loop: true
          }
        }
      }
    });

    const ctx5 = document.getElementById("mixedChart");
    const mixedChart = new Chart(ctx5, {
      data: {
        datasets: [
          {
            type: "bar",
            label: "Bar Dataset",
            data: data,
          },
          {
            type: "line",
            label: "Line Dataset",
            data: [10, 20, 30, 40, 50, 60],
          },
        ],
      },
    });

    const polarC = document.getElementById("polarChart");
    const polarChart = new Chart(polarC, {
      type: "polarArea",
      data: polarData,
      options: {},
    });

    const radarC = document.getElementById("radarChart");
    const radarChart = new Chart(radarC, {
      type: "radar",
      data: radarData,
      options: {},
    });

    const scatterC = document.getElementById('scatterChart')

    const scatterChart = new Chart(scatterC,{
      type:'scatter',
      data:scatterData,
      options:{
        
      }
    })

    myChart;
    barChart;
    bubbleChart;
    doughnutChart;
    lineChart;
    mixedChart;
    polarChart;
    radarChart;
    scatterChart
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
