<template>
    <div>
        <form @submit.prevent="sendMessage">

            <input type="text" placeholder="Cosa stai pensando?" v-model="textMessage">
            <button type="submit" class="btn btn-primary">Twitta</button>

        </form>
    </div>
</template>

<script>

export default {
    name: 'NewPost',

    created(){
        if(localStorage.token) {
            this.token = localStorage.token
        }
    },

    data() {
        return {
            textMessage: '',
            token: '',
            headers: {headers: { 'Authorization': `Bearer ${this.token}` }},
        }
    },

    computed: {
        dataMessage() {
            return {
                message: this.textMessage,
            }
        }
    },

    methods: {
        sendMessage() {
            this.$emit('sendMessage', this.dataMessage);
        }
    }
}
</script>
