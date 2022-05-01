<template>
  <div id="MIDISpace" @dragover.stop.prevent.capture="isHovering=true" @dragleave.stop.prevent.capture="isHovering=false" @drop.stop.prevent.capture="fileDrop">
    <DragnDrop v-if="!hasFile" :status="isHovering" />
  </div>
</template>

<script>
import DragnDrop from "./DragnDrop.vue";

export default {
  name: "MIDIFrame",
  created() {},
  data() {
    return {
      hasFile: false,
      isDraging: false,
      isHovering: false
    };
  },
  props: {
  },
  methods: {
  },
  components: {
    DragnDrop
  }
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