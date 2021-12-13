<template>
  <div>
      <button @click="getuser()">click</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'ListOfUsers',

    created() {
        // axios.get('http://staging.iakta.net:8000/api/listUsers')
        // .then(res => {
        //     console.log(res.data)
        // })
        // .catch(e => {
        //     console.error(e);
        // })

        if(localStorage.token) {
            this.token = localStorage.token;
        }
    },

    data() {
        return {
            list: [],
            token: '',
        }
    },

    methods: {
        getuser(){
            console.log(this.token)
            axios.get('http://staging.iakta.net:8000/api/listUsers', {
           'headers': { 'Authorization': `Bearer ${this.token}` }
          })
          .then(res=>{
            console.log(res)
          })
          .catch(e =>{
            console.log(e);
          });
    }
    }
}
</script>