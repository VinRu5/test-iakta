<template>
    <div class="post" v-for="post in posts" :key="post.id">
        <div class="post-text">{{ post.message }}</div>

        <div class="date-post">{{ post.date }}</div>
    </div>
</template>

<script>
export default {
    name: 'Post',

    props: {
        posts: Array,
    },

    data() {
        return {
        }
    }
}
</script>
