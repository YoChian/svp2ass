<script setup></script>
<template>
  <div id="EditSpace">
    <div class="TitleBar">编辑窗口</div>
  </div>
</template>

<script>
export default {
  name: "EditFrame",
  created() {},
  data() {
    return {};
  },
  props: {},
  methods: {
    fileUpload(request) {
      console.log(request.file.file);
      var reader = new FileReader(); //这里是核心！！！读取操作就是由它完成的。
      reader.readAsText(request.file.file); //读取文件的内容

      reader.onload = function () {
        console.log("读取结果：", this.result); //当读取完成之后会回调这个函数，然后此时文件的内容存储到了result中。直接操作即可。

        console.log("读取结果转为JSON：");
        let json = JSON.parse(this.result.split("\x00", 1)[0]);
        console.log(json);
      };
    },
    beforeUpload(data) {
      console.log(data);
      if (data.file.name.split(".").pop() != "svp") {
        console.error("只能上传png格式的图片文件，请重新上传", data.file);
        return false;
      }
      return true;
    },
  },
};
</script>

<style lang="scss" scoped>
#EditSpace {
  height: 100%;
  background-color: #2d2d2d;
}
</style>
