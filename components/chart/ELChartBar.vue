<template>
  <div :style="wrapperStyle">
    <canvas ref="chartRef" aria-label="Bar 차트 입니다" role="img" />
  </div>
</template>

<script>
import Chart from "chart.js/auto";

export default {
  props: {
    wrapperStyle: {
      type: Object,
      default: () => ({}),
    },
    type: {
      type: String,
      default: "bar",
    },
    data: {
      type: Object,
      default: () => ({}),
    },
    options: {
      type: Object,
      default: () => ({}),
    },
    plugins: {
      type: Array,
      default: () => [],
    },
  },
  setup(props) {
    const chartRef = ref(null);
    const chart = ref(null);

    const { wrapperStyle, type, data, options, plugins } = toRefs(props);

    const renderChart = () => {
      if (chartRef.value === null) return;

      const ctx = chartRef.value.getContext("2d");

      chart.value = new Chart(ctx, {
        type: type.value,
        data: data.value,
        options: options.value,
        plugins: plugins.value,
      });
    };

    onMounted(renderChart);

    onBeforeUnmount(() => {
      if (chart.value !== null) {
        chart.value.destroy();
      }
    });

    return {
      chartRef,
    };
  },
};
</script>
