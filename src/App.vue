<template>
  <div class="app">
    <my-dialog v-model:show="dialogVisible">
      <post-form :posts="posts" @create="createPost"/>
    </my-dialog>
    <h1 class="postsHeader">
      Список постов
    </h1>
    <my-button @click="openDialog" class="createButton">
      Создать пост
    </my-button>
    <div class="actions">
      <my-select
        v-model="selectedSort"
        :options="sortOptions"
      />
    </div>
    <post-list v-if="!isPostsLoading" :posts="posts" @remove="removePost"/>
    <my-loader v-else/>
  </div>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import type {IPost, sortPost} from './types/IPost';
import PostForm from './components/PostForm.vue'
import PostList from './components/PostList.vue';
import MyDialog from "@/UI/MyDialog.vue";
import MyButton from "@/UI/MyButton.vue";
import axios from "axios";
import MyLoader from "@/UI/MyLoader.vue";
import MySelect from "@/UI/MySelect.vue";
import type {IOption} from "@/types/IOption";

export default defineComponent({
  name: "App",
  components: {
    MySelect,
    MyLoader,
    MyButton,
    MyDialog,
    PostForm,
    PostList
  },
  data() {
    const posts: IPost[] = [];
    const dialogVisible: boolean = false
    const isPostsLoading: boolean = true
    const selectedSort: string = ''
    let sortOptions: IOption[] = [
      {value: 'title', name: 'По названию'},
      {value: 'body', name: 'По описанию'},
      {value: 'id', name: 'По id'},
    ]
    return {
      posts,
      dialogVisible,
      isPostsLoading,
      selectedSort,
      sortOptions
    }
  },
  mounted() {
    this.fetchPosts()
  },
  watch: {
    selectedSort(newValue: sortPost) {
      if (newValue !== "id") {
        this.posts.sort((post1, post2) => {
          return post1[newValue].localeCompare(post2[newValue])
        })
      } else {
        this.posts.sort((post1, post2) => {
          return post1.id < post2.id ? 1 : -1
        })
      }
    }
  },
  methods: {
    createPost(post: IPost) {
      this.posts.push(post)
      this.dialogVisible = false
    },
    removePost(post: IPost) {
      this.posts = this.posts.filter(item => {
        return item.id !== post.id
      })
    },
    openDialog() {
      this.dialogVisible = true
    },
    async fetchPosts() {
      try{
        await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=5').then((res) => {
          setTimeout(() => {
            this.posts = res.data
            this.isPostsLoading = false
          }, 1000)
        })
      } catch (e: any) {
        alert(e.message)
      }
    }
  },
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
  .createButton{
    width: 500px;
    margin-bottom: 1rem;
  }
  .actions{
    margin-bottom: 1rem;
    display: flex;
    justify-content: space-around;
    width: 750px;
  }
</style>


