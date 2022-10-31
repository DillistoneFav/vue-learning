<template>
  <div class="dialog" v-if="show" @click="hideDialog">
    <div class="content" @click.stop>
      <slot></slot>
    </div>
  </div>
</template>

<script lang="ts">
import {defineComponent} from "vue";

export default defineComponent({
  name: "my-dialog",
  props: {
    show: {
      type: Boolean,
      default: false,
    }
  },
  methods: {
    hideDialog() {
      this.$emit('update:show', false)
    }
  }
})
</script>

<style lang="scss" scoped>
  .dialog{
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(255, 255, 255, 0.20);
    position: fixed;
    display: flex;
    .content{
      margin: auto;
      background: #000;
      border-radius: 10px;
      min-height: 200px;
      min-width: 500px;
      padding: 1rem;
      border: 2px solid lightblue;
      display: flex;
      align-items: center;
    }
  }
</style>
