<template>
  <Teleport to="#teleports" v-if="teleportOpened">
    <div v-if="direction === 'left'" class="left-transition-container">
      <Transition name="left-slide">
        <div v-if="slideOpend" class="slide-layout">
          <slot />
        </div>
      </Transition>
    </div>
    <div v-else class="right-transition-container">
      <Transition name="right-slide">
        <div v-if="slideOpend" class="slide-layout">
          <slot />
        </div>
      </Transition>
    </div>
  </Teleport>
</template>

<script>
export default {
  props: {
    direction: {
      type: String,
      default: "left", // left, right
    },
  },
  exposes: ["open", "close"],
  setup(props, { emit }) {
    const allData = {
      teleportOpened: ref(false),
      slideOpend: ref(false),
    };

    const allMethods = {
      open: () => {
        allData.teleportOpened.value = true;
        nextTick(() => {
          allData.slideOpend.value = true;
        });
      },
      close: () => {
        allData.slideOpend.value = false;
        setTimeout(() => {
          allData.teleportOpened.value = false;
          // slideOpend의 변경으로 사라지는 컴포넌트의 transition 지연시간보다 반드시 크거나 같아야 한다.
        }, 300);
      },
    };

    return { ...allData, ...allMethods };
  },
};
</script>

<style lang="scss" scoped>
.left-transition-container {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
  z-index: 10000;
}

.right-transition-container {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
  z-index: 10000;
}

.slide-layout {
  height: 100%;
  background-color: beige;
  overflow: auto;
}

.left-slide-enter-active,
.left-slide-leave-active,
.right-slide-enter-active,
.right-slide-leave-active {
  transition: transform 300ms;
}

.left-slide-enter-from,
.left-slide-leave-to {
  transform: translateX(-100%);
}

.right-slide-enter-from,
.right-slide-leave-to {
  transform: translateX(100%);
}
</style>
