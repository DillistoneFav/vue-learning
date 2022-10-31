<template>
  <form @submit.prevent>
    <div class="inputsWrapper">
      <my-input
          v-model="inputValues.title"
          placeholder="Название"
      />
      <my-input
          v-model="inputValues.description"
          placeholder="Описание"
      />
    </div>
    <my-button
        @click="createPost"
        class="formButton"
    >
      Создать пост
    </my-button>
  </form>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import type {PropType} from "vue";
import type {IPost} from "@/types/IPost"
import MyInput from "@/UI/MyInput.vue";

interface inputValuesProps {
  title: string,
  description: string
}

export default defineComponent({
  name: "PostForm",
  components: {MyInput},
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
  flex-direction: column;
  height: 75px;
  justify-content: space-between;
}
form button{
  margin-top: 1rem;
}
</style>
