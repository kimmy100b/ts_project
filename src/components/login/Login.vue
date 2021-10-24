<template>
    <div>
        <h1>Login</h1>
            <div>
                <div class="Login-d-label">ID</div>
                <el-input
                    class="Login-i-input"
                    placeholder="아이디를 입력하세요"
                    type="text"
                    v-model="usrId"
                />
            </div>
            <div>
                <div class="Login-d-label">PassWord</div>
                <el-input
                    class="Login-i-input"
                    placeholder="비밀번호를 입력하세요"
                    type="password"
                    v-model="usrPwd"
                />
            </div>
        <el-button type="primary" @click="login" class="Login-btn-login">Login</el-button>
    </div>
</template>

<script lang="ts">
export default {
  props: {
    isLogin: Boolean
  },
  data (): { usrId: string; usrPwd: string } {
    return {
      usrId: '',
      usrPwd: ''
    }
  },
  methods: {
    login (): void {
      if (this.usrId === 'demo' && this.usrPwd === '1234') {
        this.$emit('setLogin', true)
        // console.log("로그인성공");
      } else {
        this.$message({
          message: 'Login Fail',
          type: 'error'
        })
      }
    }
  }
}
</script>

<style scoped>
.Login-d-label{
    margin-top: 20px;
}

.Login-i-input {
    margin-top: 5px;
}

.Login-btn-login {
    margin-top: 10px;
    float: right;
}
</style>
