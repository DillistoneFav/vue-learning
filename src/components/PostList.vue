<template>
  <div class="postsContainer" v-if="posts.length > 0">
    <post-item
        :post="post"
        v-for="post in posts"
        :key="post.id"
        @remove="$emit('remove', post)"
    />
  </div>
  <div v-else class="noPosts">
    <span>Список постов пуст</span>
  </div>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import type {PropType} from "vue";
import type {IPost} from "@/types/IPost";
import PostItem from "@/components/PostItem.vue";

export default defineComponent({
  name: "PostList",
  components: {PostItem},
  props: {
    posts: {
      type: Array as PropType<IPost[]>,
      required: true
    }
  }
})
</script>

<style scoped>
  .postsContainer{
    padding: 1rem;
    border-top: 2px solid brown;
  }
  .noPosts span{
    text-align: center;
    font-size: 24px;
    color: red;
    font-weight: bold;
  }
</style>
