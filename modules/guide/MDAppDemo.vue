<template>
  <div class="app-demo">
    <h2>AppDemo 화면입니다.</h2>
    <div style="height: 120vh; margin: 16px; background: green">
      <button @click="onClickBtnGuideHelper">AppDemo > GuideHelper 열기</button>
      <br />
      <br />
      <button @click="onClickBtnClose">닫기</button>
    </div>
    <nav class="fnb">Footer Navigator Bar 영역</nav>
  </div>
</template>

<script>
export default {
  emits: ["close", "onClickBtnGuideHelper"],
  setup(props, context) {
    const allData = {};

    const allMethods = {
      onClickBtnGuideHelper() {
        context.emit("onClickBtnGuideHelper");
      },

      onClickBtnClose() {
        context.emit("close");
      },
    };

    return { ...allData, ...allMethods };
  },
};
</script>

<style lang="scss" scoped>
.app-demo {
  // height: 100%;
  padding-bottom: 84px;
  h2 {
    padding: 16px;
    margin: 0;
  }

  .fnb {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 84px;
    background: blueviolet;
    color: white;
    // display: flex;
    // justify-content: space-around;
    // align-items: center;
  }
}
</style>
