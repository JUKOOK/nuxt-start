<template>
  <div>
    <h2>Root URL(모바일) 입니다.</h2>
    <ELChart />
  </div>
</template>

<script>
import ELChart from "@/components/chart/ELChart.vue";

export default {
  components: {
    ELChart,
  },
  setup(props) {
    definePageMeta({
      layout: "mobile",
    });
  },
};
</script>
