<template>
    <div class="row justify-content-center">
        <h1>Registrati subito!</h1>
        <form @submit.prevent="sendRegister" class="form-container col-8">
            <div class="row form-section"> 
                <label for="username" class="col-12">Username</label>
                <input 
                    type="text" 
                    id="username" 
                    name="username" 
                    class="col-12" 
                    v-model="register.username"
                />
            </div>

            <div class="row form-section">
                <label for="email" class="col-12">Email</label>
                <input 
                    type="email" 
                    id="email" 
                    name="email" 
                    class="col-12"
                    v-model="register.email"
                />
            </div>

            <div class="row form-section">
                <label for="password" class="col-12">Password</label>
                <input 
                    type="password" 
                    name="password" 
                    id="password" 
                    class="col-12"
                    v-model="register.password"
                />
            </div>

            <div class="form-section">
                <input type="submit" value="Registrati" class="btn btn-primary"> 
            </div>
        </form>

    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Register',

    data() {
        return {
            register: {},
        }
    },

    methods: {
        sendRegister() {
            console.log('register', this.register);

            axios.post('http://staging.iakta.net:8000/api/register', this.register)
            .then(res => {
                console.log(res.data);
                this.$emit('registerTrue');
            })
            .catch(e => {
                console.error(e);
            })
        }
    }

}
</script>