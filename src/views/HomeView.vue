<template>
  <div>
    <el-container>
      <el-main>
        <el-form :model="uploadInfo">
          <el-upload
            drag
            :limit="1"
            :accept="'xlsx'"
            :before-upload="handleFilePreview"
          >
            <el-icon class="el-icon-upload"></el-icon>
            <div class="el-upload__text">
              将文件拖拽到这里<em>或点击上传</em>
            </div>
          </el-upload>
          <el-form-item label="发件邮箱">
            <el-input v-model="uploadInfo.sendEmail" placeholder="请输入发件邮箱" />
          </el-form-item>
          <el-form-item label="收件邮箱">
            <el-input v-model="uploadInfo.recvEmail" placeholder="请输入收件邮箱" />
          </el-form-item>
        </el-form>

        <el-button type="primary" @click="onClickButton">发送</el-button>
      </el-main>
    </el-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      uploadInfo: {},
    };
  },
  methods: {
    onClickButton() {
      console.log(this.uploadInfo);
    },
    handleFilePreview(file) {
      console.log("0000")
      // 判断是否是xlsx文件，你可以根据需要更改文件类型判断逻辑
      if (file.type === 'applicationnd.openxmlformats-officedocument.spreadsheetml.sheet') {
        const reader = new FileReader();
        reader.onload = (e) => {
          const fileURL = e.target.result;
          // 这里可以将fileURL展示在页面上，例如使用<img>标签或<a>标签
          console.log('预览文件URL:', fileURL);
        };
        reader.readAsDataURL(file);
      } else {
        this.$message.error('请选择有效的xlsx文件');
      }
      return false; // 阻止文件上传
    },
  },
};
</script>
