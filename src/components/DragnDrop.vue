<script setup>
import { NText, useNotification, NUpload, NUploadDragger } from "naive-ui";
import { ref } from "vue";

const notification = useNotification();
</script>

<template>
  <n-upload
    id="project-uploader"
    ref="upload"
    :max="1"
    :multiple="false"
    :show-file-list="false"
    :custom-request="fileUpload"
    @before-upload="beforeUpload"
  >
    <n-upload-dragger><n-text>将工程拖入此处导入</n-text> </n-upload-dragger>
  </n-upload>
</template>

<script>
export default {
  name: "DragnDrop",
  created() {},
  data() {
    return { JSONObject: null };
  },
  props: {},
  methods: {
    fileUpload(request) {
      //从文件对象以文本形式读取数据
      const reader = new FileReader();
      reader.readAsText(request.file.file);
      //FileReader完成读取后回调setJSON
      reader.onload = (ev) => this.setJSON(ev.target.result);
      reader.onerror = (ev) => this.handleReaderError(ev.target.error);
    },
    setJSON(JSONText) {
      //将JSON字符串转换为对象
      this.JSONObject = JSON.parse(JSONText.split("\x00", 1)[0]); //剔除JSON末尾的\x00避免函数出错
      this.$emit("fileUploaded", this.JSONObject); //触发fileuploaded事件供父组件进行后续操作
    },
    handleReaderError(e) {
      this.notification.error({
        content: "FileReader错误 " + "Code " + e.code + ": " + e.name,
        meta: e.message,
        duration: 3000,
      });
      this.$refs.upload.clear();
    },
    beforeUpload(data) {
      if (data.file.name.split(".").pop() != "svp") {
        this.notification.error({
          content: "文件读取失败",
          meta: "不受支持的文件类型",
          duration: 3000,
        });
        return false;
      }
      return true;
    },
  },
};
</script>

<style lang="scss">
#project-uploader {
  height: 100%;
  .n-upload-trigger {
    width: 100%;
    height: 100%;
    .n-upload-dragger {
      display: flex;
      height: 100%;
      align-items: center;
      justify-content: center;
      .n-text {
        font-size: xxx-large;
      }
    }
  }
}
</style>
