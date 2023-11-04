<script>
import axios from 'axios';
export default {
  data() {
    return {
      uploadInfo: {

      }
    }
  },
  methods: {
    onClickButton() {
      console.log(this.uploadInfo);
    },
    onSuccessSendFile(response, uploadFile, uploadFiles) {

      if (response.message === 'success') {
        ElMessage({
          message: '发送成功!',
          type: 'success',
        })
      } else {
        ElMessage({
          message: '发送失败!' + response.data,
          type: 'error',
        })
      }

    }
  }
}
</script>

<template>
  <div>
    <el-container>
      <el-main>
        <div style="margin-top: 1rem; margin-bottom: 1rem;"> 成绩单文件导入 </div>
        <el-form :model="uploadInfo">
          <el-upload drag :limit=1 accept=".xlsx" :action="'http://127.0.0.1:5000/receive'"
            :on-success="onSuccessSendFile">
            <el-icon><upload-filled /></el-icon>
            <div class="el-upload__text">
              将文件拖拽到这里<em>或点击上传</em>
            </div>
            <template #tip>
              <div class="el-upload__tip">
                <div></div>
              </div>
            </template>
          </el-upload>
          <!-- <el-form-item label="发件邮箱">
            <el-input v-model="uploadInfo.sendEmail" placeholder="请输入发件邮箱" />
          </el-form-item>
          <el-form-item label="收件邮箱">
            <el-input v-model="uploadInfo.recvEmail" placeholder="请输入收件邮箱" />
          </el-form-item> -->
        </el-form>

        <!-- <el-button type="primary" @click="onClickButton">发送</el-button> -->
      </el-main>
    </el-container>

  </div>
</template>
