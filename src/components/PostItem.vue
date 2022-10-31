<template>
  <div class="post">
    <div class="postInfo">
      <div class="postTitleContainer"><span>Название:</span>{{post.title}}</div>
      <div class="postDescriptionContainer"><span>Описание:</span>{{post.description}}</div>
    </div>
    <div class="buttonsContainer">
      <my-button>Редактировать пост</my-button>
      <my-button class="deleteButton">Удалить пост</my-button>
    </div>
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
  width: 750px;
  border: 2px solid lightblue;
  padding: 0.5rem;
  border-radius: 10px;
  font-size: 20px;
  margin-top: 1rem;
  display: flex;
  min-height: 75px;
}
.postInfo{
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 90%;
}
.post button{
  width: 150px;
}
.post:first-of-type{
  margin-top: 0;
}
.post .postTitleContainer, .post .postDescriptionContainer{
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  word-break: break-all;
  padding-right: 0.5rem;
}
.post span{
  font-weight: bold;
  font-size: 24px;
  margin-right: 0.5rem;
}
.post .buttonsContainer{
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}
.post .buttonsContainer button:first-of-type{
  margin-bottom: 0.5rem;
}
.post .deleteButton{
  border-color: red;
}
</style>
