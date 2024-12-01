<template>
  <div>
    <h2>Root URL(모바일) 입니다.</h2>
    <Chart1 />
    <Chart2 />
    <Chart3 />
  </div>
</template>

<script>
import Chart1 from "@/modules/chart/Chart1.vue";
import Chart2 from "@/modules/chart/Chart2.vue";
import Chart3 from "@/modules/chart/Chart3.vue";

export default {
  components: {
    Chart1,
    Chart2,
    Chart3,
  },
  setup(props) {
    definePageMeta({
      layout: "mobile",
    });
  },
};
</script>
