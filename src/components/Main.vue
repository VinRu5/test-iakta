<template>
  <div class="row">
      <NewPost/>
      <Post/>

  </div>
</template>

<script>
import NewPost from './NewPost.vue'
import Post from './Post.vue'
export default {
  components: { Post, NewPost },
    name: 'Main',

}
</script>

<style>

</style>