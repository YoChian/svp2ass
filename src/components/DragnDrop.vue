<script setup>

import { NP } from 'naive-ui';

</script>

<template>
  <div id="DragBox">
    <div id="DashedBox" :class="status?'DashShow':null">
      <n-p id="DragInfo">{{status?'松开鼠标导入工程':'将工程拖入此处导入'}}</n-p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Test",
  created() {},
  data() {
    return {};
  },
  props: {
    status: Boolean
  },
  methods: {},
};
</script>

<style lang="scss" scoped>
  #DragBox {
    width: 100%;
    height: 100%;
    position: absolute;
    display: flex;
    align-items: center;
    justify-content: center;
    pointer-events: none;
  }

  #DashedBox {
    width: 95%;
    height: 80%;
    border-width: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    pointer-events: none;
  }

  .DashShow {
    border-style: dashed;
    border-color: gray;
  }

  #DragInfo {
    font-size: xxx-large;
    pointer-events: none;
    user-select:none;
  }
</style>