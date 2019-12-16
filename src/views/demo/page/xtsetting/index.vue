<template>
  <d2-container>
    <el-container>
      <el-header><img src="./02/top.png" alt=""></el-header>
      <el-main>
        <el-row :gutter="30">
          <el-col :span="8">
            <div class="grid-content bg-purple gc1">
              <div class="title">网站名称：</div>
              <el-input
                class="height2"
                placeholder="智能监测线夹"
                v-model="input"
                clearable>
              </el-input>
              <div class="title">网站地址：</div>
              <el-input
                class="height2"
                placeholder="www.it.com"
                v-model="input"
                clearable>
              </el-input>
              <div class="title">系统邮箱：</div>
              <el-input
                class="height2"
                placeholder="123@qq.com"
                v-model="input"
                clearable>
              </el-input>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content bg-purple gc2">
              <div class="title">广告语：</div>
              <el-input
                placeholder="让电的连接更加安全，快捷！"
                v-model="input"
                clearable>
              </el-input>
              <div class="title">客服热线：</div>
              <el-input
                placeholder="010-123456"
                v-model="input"
                clearable>
              </el-input>
              <div class="title">背景图片上传：</div>
              <el-upload
                class="avatar-uploader height2"
                action="https://jsonplaceholder.typicode.com/posts/"
                :show-file-list="false"
                :on-success="handleAvatarSuccess"
                :before-upload="beforeAvatarUpload">
                <img v-if="imageUrl" :src="imageUrl" class="avatar">
                <i v-else class="el-icon-plus avatar-uploader-icon"></i>
              </el-upload>
              <div class="title">首页用户标志：</div>
              <el-upload
                class="avatar-uploader height2"
                action="https://jsonplaceholder.typicode.com/posts/"
                :show-file-list="false"
                :on-success="handleAvatarSuccess"
                :before-upload="beforeAvatarUpload">
                <img v-if="imageUrl" :src="imageUrl" class="avatar">
                <i v-else class="el-icon-plus avatar-uploader-icon"></i>
              </el-upload>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="grid-content bg-purple gc3">
              <div class="title">底部版权信息：</div>
              <el-input
                placeholder="请输入内容"
                v-model="input"
                clearable>
              </el-input>
              <div class="title">公司名称：</div>
              <el-input
                placeholder="请输入内容"
                v-model="input"
                clearable>
              </el-input>
              <div class="title">备案号：</div>
              <el-input
                placeholder="请输入内容"
                v-model="input"
                clearable>
              </el-input>
              <div class="title">系统隶属公司：</div>
              <el-input
                placeholder="请输入内容"
                v-model="input"
                clearable>
              </el-input>
              <div class="title">LOGO图片上传：</div>
              <el-upload
                class="avatar-uploader height2"
                action="https://jsonplaceholder.typicode.com/posts/"
                :show-file-list="false"
                :on-success="handleAvatarSuccess"
                :before-upload="beforeAvatarUpload">
                <img v-if="imageUrl" :src="imageUrl" class="avatar">
                <i v-else class="el-icon-plus avatar-uploader-icon"></i>
              </el-upload>
            </div>
          </el-col>
        </el-row>
        <div><img style="width:80%" src="./02/xingzhuang.png" alt=""><span style="display:inline-block">保存</span></div>
      </el-main>
    </el-container>
  </d2-container>
</template>

<script>
export default {
  name: 'xtsetting',
  data () {
    return {
      input: '',
      imageUrl: ''
    }
  },
  methods: {
    handleAvatarSuccess (res, file) {
      this.imageUrl = URL.createObjectURL(file.raw)
    },
    beforeAvatarUpload (file) {
      const isJPG = file.type === 'image/jpeg'
      const isLt2M = file.size / 1024 / 1024 < 2

      if (!isJPG) {
        this.$message.error('上传头像图片只能是 JPG 格式!')
      }
      if (!isLt2M) {
        this.$message.error('上传头像图片大小不能超过 2MB!')
      }
      return isJPG && isLt2M
    }
  }
}
</script>

<style scoped>
  .el-header {
    background-color: transparent;
    text-align: center;
  }
  .el-main {
    background-color: transparent;
  }
  .el-main div span{
    width:18%;
    height:50px;
    background-image: url('./02/按钮.png');
    background-size: 100% 100%;
    background-repeat: no-repeat;
    margin-left: 2%;
    text-align: center;
    line-height: 50px;
    font-size: 22px;
    color:#fff
  }
  .el-main div span:hover{
    cursor: pointer;
  }
  .el-row {
    margin-bottom: 20px;
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: transparent;
  }
  .bg-purple {
    background: transparent;
    height: 630px;
  }
  .bg-purple-light {
    background: transparent;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
    background-size: 100% 100%;
    background-repeat: no-repeat;
    padding: 3rem;
  }
  .gc1{
    background-image: url('./02/基本信息.png');
  }
  .gc2{
    background-image: url('./02/内容信息.png');
  }
  .gc3{
    background-image: url('./02/底部信息.png');
  }
  .row-bg {
    padding: 10px 0;
    background-color: transparent;
  }
  .title{
    color: rgb(0,255,236);
    font-size: 0.8rem;
    margin: 2rem 0 1rem 0;
  }
  .height2{
    height: 4.5rem;
  }
  .avatar-uploader{
    border: 1px solid rgb(9,104,160);
    border-radius: 5px;
    display: flex;
    align-items:center;
    justify-content: center;
  }
  .el-icon-plus{
    font-size: 1.5rem;
  }
</style>
