<template>
  <select v-model="localModelValue" @change="changeOption" class="select">
    <option disabled value="">Выберите из списка</option>
    <option
        v-for="option in options"
        :key="option.value"
        :value="option.value"
    >
      {{ option.name }}
    </option>
  </select>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import type {PropType} from "vue";
import type {IOption} from "@/types/IOption";

export default defineComponent({
  name: 'my-select',
  props: {
    modelValue: {
      type: String
    },
    options: {
      type: Array as PropType<IOption[]>,
      default: () => [] as PropType<IOption[]>
    }
  },
  methods: {
    changeOption(event: Event) {
      this.$emit('update:modelValue', (event.target as HTMLSelectElement).value)
    }
  },
  computed: {
    localModelValue: {
      get() {
        return this.modelValue
      },
      set(newValue: IOption) {
        this.$emit('update:modelValue', newValue.value)
      },
    },
  },
})
</script>

<style scoped lang="scss">
  .select{
    height: 30px;
    width: 200px;
    background: none;
    color: #fff;
  }
  option{
    color: #000 !important;
  }
</style>
