<template>
  <div>
    <MDLogin
      @onClickBtnAppDemo="openAppDemo"
      @onClickBtnGuideHelper="openGuideHelper"
    />

    <!-- Left Slide, AppDemo -->
    <MDSlideLayout ref="refLeftSlide" :direction="'left'">
      <MDAppDemo
        @onClickBtnGuideHelper="openGuideHelper"
        @close="closeAppDemo"
      />
    </MDSlideLayout>

    <!-- Right Slide, GuideHelper -->
    <MDSlideLayout ref="refRightSlide" :direction="'right'">
      <MDGuideHelper @close="closeGuideHelepr" />
    </MDSlideLayout>
  </div>
</template>

<script>
import MDLogin from "@/modules/guide/MDLogin.vue";
import MDAppDemo from "@/modules/guide/MDAppDemo.vue";
import MDGuideHelper from "@/modules/guide/MDGuideHelper.vue";

import MDSlideLayout from "@/modules/guide/MDSlideLayout.vue";

export default {
  components: {
    MDLogin,
    MDAppDemo,
    MDGuideHelper,
    MDSlideLayout,
  },
  setup(props) {
    definePageMeta({
      // layout: "mobile",
    });

    const allData = {
      refLeftSlide: ref(null),
      refRightSlide: ref(null),
    };

    const allMethods = {
      openAppDemo() {
        allData.refLeftSlide.value?.open();
      },

      closeAppDemo() {
        allData.refLeftSlide.value?.close();
      },

      openGuideHelper() {
        allData.refRightSlide.value?.open();
      },

      closeGuideHelepr() {
        allData.refRightSlide.value?.close();
      },
    };

    return { ...allData, ...allMethods };
  },
};
</script>
