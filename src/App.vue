<template>
  <div>
    <login-page v-if="!isLogin"
    v-bind:isLogin="isLogin"
    @setLogin="setLogin"
    class="App-login-login"
    ></login-page>
    <main-page v-else></main-page>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import ElementUI from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'

import login from '@/components/login/Login.vue'
import main from '@/components/main/Main.vue'
import { Prop } from 'vue-property-decorator'

Vue.use(ElementUI)

export default {
  data (): { isLogin: boolean } {
    return {
      isLogin: false
    }
  },
  methods: {
    setLogin (isLogin: boolean): void {
      this.isLogin = isLogin
    }
  },
  components: {
    'login-page': login,
    'main-page': main
  }
}
</script>

<style lang="scss">
.App-login-login{
  margin: 15% 25%;
  width: 50%;
}
</style>
