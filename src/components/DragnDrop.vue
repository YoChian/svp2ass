<template>
  <div id="DragBox">
    <div id="DashedBox">
      {{DragTips}}
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
  props: {},
  methods: {},
};
</script>

<style lang="scss" scoped>
  #DragBox {
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 10%;
    position: absolute;
  }

  #DashedBox {
    width: 100%;
    height: 100%;
    border-width: 10px;
    border-style: dashed;
    border-color: gray;
  }
</style>