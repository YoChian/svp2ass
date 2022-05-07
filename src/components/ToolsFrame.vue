<script setup>
import { NButtonGroup, NButton, NIcon, NSpace } from "naive-ui";
import { Play28Filled, Pause24Filled, Stop24Filled } from "@vicons/fluent";
</script>

<template>
  <n-space id="ToolsSpace" justify="space-between">
    <div id="LeftTools">
      <n-button-group>
        <n-button quaternary> 文件 </n-button>
        <n-button quaternary> 关于 </n-button>
      </n-button-group>
    </div>
    <div id="MidTools">
      <n-button-group>
        <n-button round secondary type="success">
          <n-icon> <Play28Filled /></n-icon>
        </n-button>
        <n-button round secondary type="warning">
          <n-icon><Pause24Filled /></n-icon>
        </n-button>
        <n-button round secondary type="error">
          <n-icon><Stop24Filled /></n-icon>
        </n-button>
      </n-button-group>
    </div>
    <div id="RightTools">
      <n-button text @click="$emit('change-theme')">深色</n-button>
    </div>
  </n-space>
</template>

<script>
export default {
  emits: ["change-theme"],
  methods: {},
};
</script>

<style lang="scss" scoped>
$ToolsPaddingHeight: 3px;
$ToolsPaddingWidth: 3px;

#ToolsSpace {
  padding-top: $ToolsPaddingHeight;
  padding-bottom: $ToolsPaddingHeight;
  padding-left: $ToolsPaddingWidth;
  padding-right: $ToolsPaddingWidth;
  align-items: center;
}

#RightTools {
  margin-right: 15px;
}
</style>
