<template>
  <div class="postsContainer">
    <post-item
        :post="post"
        v-for="post in posts"
    />
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
</style>
