<script setup>
  import { NButtonGroup, NButton } from 'naive-ui';
  import { NSpace } from 'naive-ui';
  import IconPlay from './icon/IconPlay.vue';
  import IconPause from './icon/IconPause.vue';
  import IconStop from './icon/IconStop.vue';
</script>

<template>
  <n-space id="ToolsFrame" justify="space-between">
    <div id="LeftTools">
      <n-button text>
        文件
      </n-button>
    </div>
    <div>
      <n-button-group id="MidTools">
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
  #ToolsFrame {
    margin-top: 10%;
    height: auto;
    width: auto;
    background-color: #323232;
    align-items: center;
  }

  $ToolsBorder:10px;

  #LeftTools {
    padding-left: $ToolsBorder;
  }

  #RightTools {
    padding-right: $ToolsBorder;
  }

  #MidTools {
    width: auto;
  }
</style>