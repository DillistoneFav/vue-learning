<script lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import {defineComponent} from "vue";

export default defineComponent({
  name: "App",
  components: {},
  data() {
    let likes: number = 0
    return {
      likes,
    }
  },
  methods: {
    addLike() {
      this.likes += 1
    },
  }
})
</script>

<template>
  <div class="app">
    <button @click="addLike">add like</button>
    <div>{{likes}}</div>
  </div>
</template>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .app{
    width: 100%;
    height: 100vh;
    background: #000;
    color: #fff;
    display: flex;
    align-items: center;
    flex-direction: column;
  }
</style>


