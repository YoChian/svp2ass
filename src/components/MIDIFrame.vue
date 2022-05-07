<template>
  <div id="MIDISpace">
    <DragnDrop v-if="!hasFile" @file-uploaded="analyseFile" />
  </div>
</template>

<script>
import DragnDrop from "./DragnDrop.vue";

import { NNotificationProvider } from "naive-ui";
export default {
  name: "MIDIFrame",
  created() {},
  data() {
    return {
      hasFile: false,
    };
  },
  props: {},
  methods: {
    analyseFile(dataObject) {
      //TODO:分析svp并使用数据生成MIDI
      console.log(dataObject);
    },
  },
  components: {
    DragnDrop,
    NNotificationProvider,
  },
};
</script>

<style lang="scss" scoped>
#MIDISpace {
  position: relative;
  width: 100%;
  height: 100%;
  background-color: #252525;
}
</style>
