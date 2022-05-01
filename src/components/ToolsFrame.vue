<script setup>
  import { NButtonGroup, NButton } from 'naive-ui';
  import { NSpace } from 'naive-ui';
  import IconPlay from './icon/IconPlay.vue';
  import IconPause from './icon/IconPause.vue';
  import IconStop from './icon/IconStop.vue';
</script>

<template>
  <n-space id="ToolsSpace" justify="space-between">
    <div id="LeftTools">
    <n-button-group>
      <n-button quaternary>
        文件
      </n-button>
      <n-button quaternary>
        关于
      </n-button>
    </n-button-group>
    </div>
    <div id="MidTools">
      <n-button-group>
        <n-button round secondary type="success">
          <IconPlay />
        </n-button>
        <n-button round secondary type="warning">
          <IconPause />
        </n-button>
        <n-button round secondary type="error">
          <IconStop />
        </n-button>
      </n-button-group>
    </div>
    <div id="RightTools">
      <n-button text>深色</n-button>
    </div>
  </n-space>
</template>

<script>
export default {
  name: "ToolsFrame",
  created() {},
  data() {
    return {};
  },
  props: {},
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
</style>