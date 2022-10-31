<template>
  <button>
    <slot></slot>
<!--    slot - kind of children     -->
  </button>
</template>

<script lang="ts">
import {defineComponent} from "vue";

export default defineComponent({
  name: "my-button"
})
</script>

<style scoped>
button{
  outline: none;
  background: none;
  color: #fff;
  border-radius: 10px;
  border: 2px solid #fff;
  padding: 5px;
  cursor: pointer;
}
</style>
