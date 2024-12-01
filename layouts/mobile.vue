<template>
  <!-- mobile 레이아웃 -->
  <div class="mobile-device-container">
    <slot />
  </div>
</template>

<script>
export default {
  setup() {
    useHead({
      htmlAttrs: {
        style: {
          height: "100vh",
          "background-color": "#1d1b1b",
        },
      },
      bodyAttrs: {
        style: {
          width: "100%",
          height: "100%",
          margin: "0",
        },
      },
    });
  },
};
</script>

<style lang="scss" scoped>
.mobile-device-container {
  width: 432px;
  height: 720px;
  overflow-y: auto;
  background-color: #fff;
  border-radius: 20px;
  box-shadow: 0 0 10px rgba(255, 255, 255, 0.1);
  padding: 16px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
