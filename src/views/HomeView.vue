<script>
export default{
  data(){
    return {
      uploadInfo:{

      }
    }
  },
  methods:{
    onClickButton(){
      console.log(this.uploadInfo);
    }
  }
}
</script>

<template>
  <div>
    <el-container>
      <el-main>
        <el-form :model="uploadInfo" >
          <el-upload drag :limit='1' :accept="xlsx">
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
