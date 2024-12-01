<template>
  <div>
    <ELChartBar
      :wrapper-style="wrapperStyle"
      :type="type"
      :data="data"
      :options="options"
      :plugins="plugins"
    />
  </div>
</template>

<script>
import ELChartBar from "@/components/chart/ELChartBar.vue";

import { valueOrDefault } from "chart.js/helpers";

export default {
  components: {
    ELChartBar,
  },
  setup() {
    const rand = (min, max) => {
      let _seed = Date.now();
      min = valueOrDefault(min, 0);
      max = valueOrDefault(max, 0);
      _seed = (_seed * 9301 + 49297) % 233280;
      return min + (_seed / 233280) * (max - min);
    };

    const annotation1 = {
      type: "line",
      borderColor: "black",
      borderWidth: 5,
      click: function ({ chart, element }) {
        console.log("Line annotation clicked");
      },
      label: {
        backgroundColor: "red",
        content: "Test Label",
        display: true,
      },
      scaleID: "y",
      value: rand(-100, 100),
    };

    const annotation2 = {
      type: "box",
      backgroundColor: "rgba(101, 33, 171, 0.5)",
      borderColor: "rgb(101, 33, 171)",
      borderWidth: 1,
      click: function ({ chart, element }) {
        console.log("Box annotation clicked");
      },
      drawTime: "beforeDatasetsDraw",
      xMax: "Orange",
      xMin: "Blue",
      yMax: rand(100, 200),
      yMin: rand(0, 100),
      xScaleID: "x",
      yScaleID: "y",
    };

    const wrapperStyle = ref({
      width: "100%",
      height: "100%",
      padding: "16px",
    });
    const type = ref("bar");
    const data = ref({
      labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
      datasets: [
        {
          label: "# of Votes",
          data: [122, 159, 13, 335, 22, 53],
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
    });
    const options = ref({
      scales: {
        y: {
          beginAtZero: true,
        },
      },
      plugins: {
        annotation: {
          annotations: {
            annotation1,
            annotation2,
          },
        },
      },
    });
    const plugins = ref([]);

    return {
      wrapperStyle,
      type,
      data,
      options,
      plugins,
    };
  },
};
</script>

<style lang="scss" scoped></style>
