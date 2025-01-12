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
      padding: "12px",
    });
    const type = ref("bar");
    const data = ref({
      labels: ["1월", "2월", "3월", "4월", "5월", "6월", "7월"],
      datasets: [
        {
          data: [
            {
              x: "1월",
              netValue: 28000,
              baseValue: 7000,
            },
            {
              x: "2월",
              netValue: 32000,
              baseValue: 8000,
            },
            {
              x: "3월",
              netValue: 36000,
              baseValue: 9000,
            },
            {
              x: "4월",
              netValue: 40000,
              baseValue: 10000,
            },
            {
              x: "5월",
              netValue: 44000,
              baseValue: 11000,
            },
            {
              x: "6월",
              netValue: 48000,
              baseValue: 12000,
            },
            {
              x: "7월",
              netValue: 52000,
              baseValue: 13000,
            },
          ],
          backgroundColor: "rgba(255, 99, 132, 0.2)",
          hoverBackgroundColor: "rgba(255, 99, 132, 0.4)",
          borderRadius: 8,
          barThickness: 16,
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
