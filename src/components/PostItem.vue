<template>
  <div class="post">
    <div><span>Название:</span>{{post.title}}</div>
    <div><span>Описание:</span>{{post.description}}</div>
  </div>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import type {PropType} from "vue";
import type {IPost} from "@/types/IPost";

export default defineComponent({
  name: "PostItem",
  props: {
    post: {
      type: Object as PropType<IPost>,
      required: true
    }
  }
})
</script>

<style scoped>
.post{
  width: 500px;
  border: 2px solid lightblue;
  padding: 0.5rem;
  border-radius: 10px;
  font-size: 20px;
  margin-top: 1rem;
}
.post:first-of-type{
  margin-top: 0;
}
.post span{
  font-weight: bold;
  font-size: 24px;
  margin-right: 0.5rem;
}
</style>
