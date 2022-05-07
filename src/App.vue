<script setup>
import { zhCN, dateZhCN } from "naive-ui";
import {
  NLayout,
  NLayoutHeader,
  NLayoutContent,
  NLayoutFooter,
  NLayoutSider,
  NSpace,
  NNotificationProvider,
} from "naive-ui";
import { defineComponent, computed } from "vue";
import { darkTheme, useOsTheme, NConfigProvider } from "naive-ui";
//导入自定义的组件
import ToolsFrame from "./components/ToolsFrame.vue";
import MIDIFrame from "./components/MIDIFrame.vue";
import PreviewFrame from "./components/PreviewFrame.vue";
import EditFrame from "./components/EditFrame.vue";
</script>

<script>
export default {
  data() {
    //根据系统主题设置深色模式
    return {
      // TODO:需要实现Light Theme样式，在此之前默认只使用Dark Theme
      usingTheme: useOsTheme().value === "dark" ? darkTheme : darkTheme,
    };
  },
  methods: {
    changeTheme() {
      this.usingTheme = this.usingTheme == null ? darkTheme : null;
    },
  },
};
</script>

<template>
  <n-config-provider
    :locale="zhCN"
    :datelocale="dateZhCN"
    :theme="usingTheme"
    :theme-overrides="{ common: { fontWeightStrong: '600' } }"
  >
    <n-notification-provider :to="'body'" :max="3" :placement="'bottom-right'">
      <n-layout
        id="AppFrame"
        position="absolute"
        content-style="display:flex; flex-direction:column"
      >
        <n-layout-header id="ToolsFrame">
          <ToolsFrame @change-theme="changeTheme" />
        </n-layout-header>
        <n-layout-content id="MidFrame" content-style="display:flex; width:100vw">
          <div id="PreviewFrame">
            <PreviewFrame />
          </div>
          <div id="EditFrame">
            <EditFrame />
          </div>
        </n-layout-content>
        <n-layout-footer id="MIDIFrame">
          <MIDIFrame />
        </n-layout-footer>
      </n-layout>
    </n-notification-provider>
  </n-config-provider>
</template>

<style lang="scss">
#app {
  font-family: Lato, FiraCode;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#AppFrame {
  height: 100vh;
}

#ToolsFrame {
  height: auto;
  background-color: #323232;
}

#MIDIFrame {
  height: 35vh;
  min-height: 100px;
  background-color: #000000;
  padding: 1px;
}

#PreviewFrame {
  width: 150%;
  background-color: #000000;
  padding: 1px;
}

#EditFrame {
  width: inherit;
  background-color: #000000;
  padding: 1px;
}

.TitleBar {
  $TapRadius: 0px;
  $TapMargin: 0px;
  background-color: #424242;
  margin-left: $TapMargin;
  margin-right: $TapMargin;
  border-top-left-radius: $TapRadius;
  border-top-right-radius: $TapRadius;
}

@font-face {
  font-family: wavefont;
  src: url(../static/wavefont.woff2) format("woff2");
}

@font-face {
  font-family: blank;
  /* src: url(./AdobeBlank2VF.ttf.woff2); */
  src: url(data:application/x-font-woff;charset=utf-8;base64,d09GMgABAAAAAARMABMAAAAAC1AAAAPjAAEAxQAAAAAAAAAAAAAAAAAAAAAAAAAAGUYcID9IVkFSVAZgP1NUQVQkP1ZWQVJjAIIAL0YKWFwwLgE2AiQDCAsGAAQgBYsyBzEXJBgIGwEKEcXkJfmqgCdD4yWAULaeeBovVzstIc6riunXpnmtXivg+BLWsFA1x8PTXP+eO5PNAn8AUCwJsYCgqxxZ1JUELrLsXkOo3TUpDjbRB8Tvo61HSFe6NVBVO1SvlxDEvYxsxE4DfNN8ImIOJ0gqtv/9fq0+Wat/NsTds46FRuqU8lf0gse1iqY3dLfkGRqhqiTVConpREoxCY1FPHelp1Ny+uwFWpZYoBA7dh04oaUEhFLUFDri7o2bj2BaFYGOOeZ1vLhvdQ0IMAUABHoC6yWZLbYAgJ9NX06XhIBcaa5iDdL76Qz2k7njkrV+ci1cx5uLNbeOtx22hbrOrMaqxrO/9QL9NwVgAUJoSZgClkjP3HjyTmDP7j0nIoQAM3AGAJfCk0F+cI8EIeugpw/+AUwGvq0R/IaJbxBM/EE9gRAIQEJCRkaBAg00UKJEE0200EIbbXTQQRdd9NBDH30MMMAQQ4wwEuEmSaYkBnnYDCBXEDnpwW9EJK5WZJBAgQZGmA0oQIMiXw91sjku790e3LzZfHZ461Z5+/ozFVTN2diLFz9/ql67cl8k+nvMWO4OBBKYtXsY6LwaespXbYFXt+TqtTcIhK83bvTx5eGGf1s5V/D9qt/p9najlt/Mj6KUQFCxsYrB4sZY4VoloVbYkpHGKGGx3RT/yaJo4wSfCEucQDLwLLLV3u5asKHhhk9QmpVZaOnEerTNyqaunQW61ucM+umj+BAD6xtRwIJe7SdfPJ0j6BTPIkzxelO3WVhf//c2jpwWnwkGXVHJ7/FoDWDAQVkQ+OBTFKZJu8lXljDZnk7YqITmExH/y0MxUyoCDOBqChwdIU8mZhKKCJ2upGVgbGinpSoKOgThuVdIkAJUCkD1UYqNlj3J5kSRrqElYYogo7sLvSE3eCVefdEJa/SRA1H0BWVMIMAKSoG1TMqBSbtr5Q+DNGe+gASmqJQCTiiX8mISEDDtHgvYUEpCDjCuCZD0oQJ1YQ3sjHRPlXdfK+E/rSY28Bg4cI6cV00RDZaMcjGklsyXggUDJ2BRVwCGvwLAfxa/WTib27k4LwoOHB0NbJMLE/HNdo7AyM7W2AINfIZwPg2I0KNAtGALqE+jIEEkfiTfWAAkgSiiBZJkLDgSCXf6EaZ2NnDRspAUq7MFXOYSaLDGnozJK4dkPCmTRSmRKSxxWiDAMFMxKVLnoZ7iPA0oLgj+UBlRkrmlg3DbW9ieSDMnJbu4KqNIxL1kjISZ9GjJ5+t2TALq0U3AcYLmZeFeX9Ww6+F30lD/+kXetcg6ZJg3EalzO/5jvn7dbo3cSO6f/4dc8dJzzBkJMwsAAAA=)
    format("woff2");
}

.wavefont {
  font-family: wavefont, blank;
  --wdth: 10;
  font-variation-settings: "wdth" var(--wdth), "algn" 0.5, "radi" 30;
}
</style>
