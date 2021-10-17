<template>
  <div>
    <login v-if="!isLogin" ref='isLogin' class="App-login-login"></login>
    <main-page v-else></main-page>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator'
import ElementUI from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'

// import Normal from '@/components/layout/Normal.vue'
import login from '@/components/login/Login.vue'
import mainPage from '@/components/main/MainPage.vue'

Vue.use(ElementUI)

@Component({
  components: {
    login: login,
    'main-page': mainPage
  }
})
export default class App extends Vue {
  @Prop() private isLogin = false
}
</script>

<style lang="scss">
.App-login-login{
  margin: 15% 25%;
  width: 50%;
}
</style>
