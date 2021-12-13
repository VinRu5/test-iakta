<template>
    <div class="post" v-for="post in posts" :key="post.id">
        <div class="post-text">{{ post.message }}</div>

        <div class="date-post">{{ post.date }}</div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Post',

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
            token: '',
            posts: [],
        }
    }
}
</script>
