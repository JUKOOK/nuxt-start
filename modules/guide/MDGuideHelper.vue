<template>
  <div>
    <h2>GuideHelper 화면입니다.</h2>
    <div style="height: 120vh; margin: 16px; background: pink">
      <button @click="onClickBtnClose">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  emits: ["close"],
  setup(props, context) {
    const allData = {};

    const allMethods = {
      onClickBtnClose() {
        context.emit("close");
      },
    };

    return { ...allData, ...allMethods };
  },
};
</script>
