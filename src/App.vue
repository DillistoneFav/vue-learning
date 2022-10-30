<script lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import {defineComponent} from "vue";

export default defineComponent({
  name: "App",
  components: {},
  data() {
    return {
      likes: 0,
    }
  }
})
</script>

<template>
  <div>{{ likes }}</div>
</template>


