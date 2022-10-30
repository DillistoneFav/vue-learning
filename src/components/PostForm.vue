<template>
  <form @submit.prevent>
    <div class="inputsWrapper">
      <input
          v-model="inputValues.title"
          type="text"
          class="inputForPosts"
          placeholder="Название"
      />
      <input
          v-model="inputValues.description"
          type="text"
          class="inputForPosts"
          placeholder="Описание"
      >
    </div>
    <button @click="createPost">Создать пост</button>
  </form>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import type {PropType} from "vue";
import type {IPost} from "@/types/IPost"

interface inputValuesProps {
  title: string,
  description: string
}

export default defineComponent({
  name: "PostForm",
  props: {
    posts: {
      type: Array as PropType<IPost[]>,
      required: true
    },
  },
  data() {
    const inputValues: inputValuesProps = {} as inputValuesProps
    return {
      inputValues
    }
  },
  methods: {
    createPost(event: PointerEvent) {
      let newPost = {
        id: Math.max(...this.posts.map(item => item.id), 0) + 1,
        title: this.inputValues.title,
        description: this.inputValues.description
      }
      this.$emit('create', newPost)
      this.inputValues = {} as inputValuesProps
    },
  }
})
</script>

<style scoped>
form{
  width: 500px;
  display: flex;
  flex-direction: column;
  margin-bottom: 1rem;
}
form .inputsWrapper{
  display: flex;
  justify-content: space-between;
}
form input{
  width: 49%;
  height: 30px;
  background: none;
  outline: none;
  color: #fff;
  border-bottom: 2px solid #fff;
  border-top: none;
  border-right: none;
  border-left: none;
}
form button{
  margin-top: 1rem;
  outline: none;
  background: none;
  color: #fff;
  border-radius: 10px;
  border: 2px solid #fff;
  height: 30px;
  cursor: pointer;
}
</style>
