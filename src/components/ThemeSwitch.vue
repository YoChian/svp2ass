<template>
  <n-button @click="SwitchThemeMode">

  </n-button>
</template>

<script>
import { NButton } from "naive-ui";
import IconLightMode from "./icon/IconLightMode.vue";
import IconDarkMode from "./icon/IconDarkMode.vue";

function SwitchThemeMode() {
  if (this.Theme==="darkTheme") {
    this.Theme=null
  } else {
    this.Theme="darkTheme"
  }
}

export default {
  name: "ThemeSwitch",
  created() {},
  data() {
    return {};
  },
  props: {
    Theme: String,
  },
  methods: {},
  components: {
    NButton,
    IconLightMode,
    IconDarkMode
  }
};
</script>

<style lang="scss" scoped>

#ThemeButton {
  overflow: hidden;
}

</style>