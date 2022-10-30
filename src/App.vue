<script lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import {defineComponent} from "vue";

export default defineComponent({
  name: "App",
  components: {},
  data() {
    return {
      likes: 0,
      dislikes: 5,
    }
  },
  methods: {
    addLike() {
      this.likes += 1
    },
    addDislike() {
      this.dislikes += 1
    }
  }
})
</script>

<template>
  <div>
    <button @click="addLike">add like</button>
    <button @click="addDislike">add dislike</button>
  </div>
  <div>
    likes: {{ likes }}<br/>
    dislikes: {{ dislikes }}
  </div>
</template>


