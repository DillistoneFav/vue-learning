<template>
  <div class="app">
    <h1 class="postsHeader">Список постов</h1>
    <post-form
        :posts="posts"
        @create="createPost"
    />
    <post-list
        :posts="posts"
    />
  </div>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import type { IPost } from './types/IPost';
import PostForm from './components/PostForm.vue'
import PostList from './components/PostList.vue';

export default defineComponent({
  name: "App",
  components: {
    PostForm,
    PostList
  },
  data() {
    const posts: IPost[] = [
      {id: 0, title: "post n1", description: "just first post"},
      {id: 1, title: "post n2", description: "just second post"},
      {id: 2, title: "post n3", description: "just third post"},
    ]
    return {
      posts,
    }
  },
  methods: {
    createPost(post: IPost) {
      this.posts.push(post)
    }
  }
})
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
</style>

<style scoped>
  .app{
    width: 100%;
    height: 100vh;
    background: #000;
    color: #fff;
    display: flex;
    align-items: center;
    flex-direction: column;
    overflow-y: auto;
  }
  .postsHeader{
    font-size: 45px;
    margin-bottom: 1rem;
  }
</style>


