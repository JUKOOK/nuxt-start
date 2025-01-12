<template>
  <div>로그인 화면입니다.</div>
  <button @click="onClickBtnAppDemo">AppDemo 열기</button>
  <button @click="onClickBtnGuideHelper">GuideHelper 열기</button>
</template>

<script>
export default {
  components: {},
  emits: ["onClickBtnAppDemo", "onClickBtnGuideHelper"],
  setup(props, context) {
    const allData = {};

    const allMethods = {
      onClickBtnAppDemo() {
        context.emit("onClickBtnAppDemo");
      },
      onClickBtnGuideHelper() {
        context.emit("onClickBtnGuideHelper");
      },
    };

    return { ...allData, ...allMethods };
  },
};
</script>

<style lang="scss" scoped></style>
