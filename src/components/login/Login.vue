<template>
    <div>
        <h1>Login</h1>
        <form>
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
        </form>
        <el-button type="primary" @click="login" class="Login-btn-login">Login</el-button>
    </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator'

@Component
export default class Login extends Vue {
    @Prop() private usrId!: string
    @Prop() private usrPwd!: string

    login (): void { // void가 없을 시
      if (this.usrId === 'demo') {
        if (this.usrPwd === '1234') {
          console.log('로그인 성공')
        //   this.$emit.isLogin = true
        //   this.$router.push('main')
        }
      } else {
        alert('아이디 및 비밀번호가 다릅니다.')
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
