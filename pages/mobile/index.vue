<template>
  <div>
    <h2>Root URL(모바일) 입니다.</h2>
    <Chart1 />
  </div>
</template>

<script>
import Chart1 from "@/modules/chart/Chart1.vue";

export default {
  components: {
    Chart1,
  },
  setup(props) {
    definePageMeta({
      layout: "mobile",
    });
  },
};
</script>
