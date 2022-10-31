<template>
  <input
      :value="modelValue"
      @input="updateInput"
      type="text"
      class="inputForPosts"
  />
</template>

<script lang="ts">
import {defineComponent} from "vue";

export default defineComponent({
  name: "my-input",
  props: {
    modelValue: [String, Number]
  },
  methods: {
    updateInput(event: Event) {
      this.$emit('update:modelValue', (event.target as HTMLInputElement).value)
    }
  }
})
</script>

<style scoped>
input{
  height: 30px;
  background: none;
  outline: none;
  color: #fff;
  border-bottom: 2px solid #fff;
  border-top: none;
  border-right: none;
  border-left: none;
}
</style>
