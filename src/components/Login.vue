<template>
  <div class="login_container">
    <div class="login_box">
<!--      头像区-->
      <div class="avatar_box">
        <img src="../assets/logo.png" alt="">
      </div>
<!--      登陆表单区-->
      <el-form ref="loginFormRef" :model="loginForm" label-width="0px" class="login_form">
<!--        用户名-->
        <el-form-item>
          <el-input v-model="loginForm.username" prefix-icon="el-icon-user"></el-input>
        </el-form-item>
<!--        密码-->
        <el-form-item>
          <el-input v-model="loginForm.password" prefix-icon="el-icon-lock" type="password"></el-input>
        </el-form-item>
<!--       按钮 -->
        <el-form-item class="btns">
          <el-button type="primary" @click="login">登陆</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      // 登陆表单的数据绑定对象
      loginForm: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    login () {
      // async表示为异步请求
      this.$refs.loginFormRef.validate(async (valid) => {
        // eslint-disable-next-line no-useless-return
        if (!valid) return
        // const { data: result } = await this.$http.post('login', this.loginForm)
        // console.log(result)
        // if (result == null || result.meta.status !== 200) return this.$message.error('登陆失败')
        this.$message.success('登陆成功')
        // 将token保存下来
        // window.sessionStorage.setItem('token', result.data.token)
        // debug
        window.sessionStorage.setItem('token', 'asdasdasd')
        await this.$router.push('/home')
      })
    }
  }
}
</script>

<style lang="less" scoped>
.login_container{
  background-color: cadetblue;
  height: 100%;
}
.login_box{
  width: 450px;
  height: 300px;
  background-color: antiquewhite;
  border-radius: 3px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%,-50%);
}
.avatar_box{
  height: 130px;
  width: 130px;
  border: 1px solid #eee;
  border-radius: 50%;
  padding: 10px;
  box-shadow: 0 0 10px #ddd;
  position: absolute;
  left: 50%;
  transform: translate(-50%,-50%);
  background-color: antiquewhite;
  img{
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background-color: beige;
  }
}
.login_form{
  position: absolute;
  bottom: 0;
  width: 100%;
  padding: 0 20px;
  box-sizing: border-box;
}
.btns{
  display: flex;
  justify-content: center;
}
</style>
