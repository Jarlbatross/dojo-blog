<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error"> {{error}} </div>
    <div v-if="posts.length">
    <PostList v-if="showPosts" :posts="posts"/>
    </div>
    <div v-else>Loading...</div>
    <button @click="togglePost">Toggle Post</button>
    <button @click="posts.pop()">Delete Post</button>
  </div>
</template>

<script>
import PostList from '@/components/PostList.vue';
import getPosts from '@/composables/getPosts'

export default {
    name: 'HomeView',
    components: { PostList },
    methods: {
      togglePost() {
        this.showPosts = !this.showPosts
      }
    },
  setup() {
    const { posts, error, showPosts, load } = getPosts()

    load() 

    return { posts, error, showPosts };
  },
}

</script>
