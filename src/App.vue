<template>
  <div class="container">
    <Register/>
  </div>
</template>

<script>
import Register from './components/Register.vue'


export default {
  name: 'App',
  components: {
    Register
    
  }
}
</script>

<style lang="scss">
  @import './style/app.scss';
</style>
