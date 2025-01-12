<template>
  <div>
    <h2>Stack Bar 차트 입니다.</h2>
    <Chart4 />
  </div>
</template>

<script>
import Chart4 from "@/modules/chart/Chart4.vue";

export default {
  components: {
    Chart4,
  },
  setup(props) {
    definePageMeta({
      layout: "mobile",
    });
  },
};
</script>
