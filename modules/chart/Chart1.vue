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

export default {
  components: {
    ELChartBar,
  },
  setup() {
    const wrapperStyle = ref({
      width: "100%",
      height: "100%",
      padding: "20px",
    });
    const type = ref("bar");
    const data = ref({
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
    });
    const options = ref({
      scales: {
        y: {
          beginAtZero: true,
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
