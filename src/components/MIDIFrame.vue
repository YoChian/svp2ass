<template>
  <div id="MIDIFrame" @dragover="fileDragOver" @dragleave="fileDragLeave" @drop="fileDrop">
    <DragnDrop v-if="isDraging" :status="isHovering" />
  </div>
</template>

<script>
import DragnDrop from "./DragnDrop.vue";

export default {
  name: "MIDIFrame",
  created() {},
  data() {
    return {};
  },
  props: {
    isDraging: Boolean,
    isHovering: Boolean
  },
  methods: {},
  components: {
    DragnDrop
  }
};

function fileDragOver(e) {
  e.stopPropagation();
  e.preventDefault();
}
</script>

<style lang="scss" scoped>
  #MIDIFrame {
    height: 40%;
    width: auto;
    background-color: #2d2d2d;
  }
</style>