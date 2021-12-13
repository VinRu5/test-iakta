<template>
  <div class="container">
    <!-- <Register
      v-if="show.register"
      @registerTrue="viewLogin"
    />-->
    <Login 
      v-if="show.login"
      @loginTrue="viewContent"
    />
    <Main 
      v-if="show.content"
    /> 
  </div>
</template>

<script>

import Login from './components/Login.vue'
// import Register from './components/Register.vue'
import Main from './components/Main.vue'


export default {
  name: 'App',
  components: {
    // Register,
    Login,
    Main
    
  },

  data() {
    return {
      show: {
        register: true,
        login: true,
        content: false,
      }
    }
  },

  methods: {
    viewLogin(){
      this.show = {
        register: false,
        login: true,
        content: false,
      }
    },

    viewContent() {
      this.show = {
        register: false,
        login: false,
        content: true,
      }
    }
  }
}
</script>

<style lang="scss">
  @import './style/app.scss';
</style>
