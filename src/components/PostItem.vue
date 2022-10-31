<template>
  <div class="post">
    <div class="postInfo">
      <div class="postTitleContainer"><span>Название:</span>{{post.title}}</div>
      <div class="postDescriptionContainer"><span>Описание:</span>{{post.body}}</div>
    </div>
    <div class="buttonsContainer">
      <my-button>Редактировать пост</my-button>
      <my-button
          class="deleteButton"
          @click="$emit('remove', post)"
      >
        Удалить пост
      </my-button>
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
  margin-right: 0.5rem;
  border-right: 2px solid lightblue;
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
  word-break: normal;
  padding-right: 0.5rem;
}
.post .postTitleContainer{
  border-bottom: 2px solid lightblue;
  padding-bottom: 0.5rem;
}
.post .postDescriptionContainer{
  padding-top: 0.5rem;
}
.post span{
  font-weight: bold;
  font-size: 24px;
  margin-right: 0.5rem;
}
.post .buttonsContainer{
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.post .buttonsContainer button:first-of-type{
  margin-bottom: 0.5rem;
}
.post .deleteButton{
  border-color: red;
}
</style>
