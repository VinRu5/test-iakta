<template>
  <div class="row">
      <NewPost
        @sendMessage="sendMessage"
      />
      <Post 
        :posts="posts"
      />

  </div>
</template>

<script>
import NewPost from './NewPost.vue'
import Post from './Post.vue'
export default {
  components: { Post, NewPost },
    name: 'Main',
    props: {
        posts: Array,

    },

    methods: {
        sendMessage(dataMessage) {
            this.$emit('sendMessage', dataMessage)
        }
    }

}
</script>

<style>

</style>