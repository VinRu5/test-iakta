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
      :posts="posts"
      @sendMessage="sendMessage"
    /> 
  </div>
</template>

<script>
import axios from 'axios';

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

  created() {

        if(localStorage.token) {
            this.token = localStorage.token;
        }

        axios.get('http://staging.iakta.net:8000/api/posts', {
           'headers': { 'Authorization': `Bearer ${this.token}` }
          })
          .then(res=>{
            this.posts = res.data;
          })
          .catch(e =>{
            console.log(e);
          });
    },

  data() {
    return {
      show: {
        register: true,
        login: true,
        content: false,
      },

      posts: []
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
    },

    sendMessage(dataMessage) {
      console.log('now', dataMessage)
      axios.post('http://staging.iakta.net:8000/api/postMessage', dataMessage, 
            {headers: { 'Authorization': `Bearer ${this.token}` }})
            .then(res=> {
              console.log(res)
                axios.get('http://staging.iakta.net:8000/api/posts', {
           'headers': { 'Authorization': `Bearer ${this.token}` }
          })
          .then(res=>{
            this.posts = res.data;
          })
          .catch(e =>{
            console.log(e);
          });
            })
            .catch(e => {
                console.log(e)
            })
    }
  }
}
</script>

<style lang="scss">
  @import './style/app.scss';
</style>
