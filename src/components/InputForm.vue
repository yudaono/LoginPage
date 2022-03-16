<script setup lang="ts">
import { toRefs } from 'vue'

const emit = defineEmits(['update:modelValue'])

const props = defineProps({
  placeholder: {
    type: String
  },
  label: { 
    type: String
  },
  type: {
    type: String
  },
  modelValue: { 
    type: [String, Number],
    default: ''
  }
})

const { modelValue, placeholder, label, type } = toRefs(props)

const inputOnChange = (event: Event) => {
  //@ts-ignore
  const value = event.target.value as String
  emit('update:modelValue', value)
}

</script>

<template>
  <label
    class="block uppercase text-gray-500 text-xs font-medium ml-4 mb-2"
    for="grid-password"
  >{{ label }}</label>
  <input
    :value="modelValue"
    @input="inputOnChange"
    :type="type"
    class="px-4 py-3 placeholder-gray-400 text-gray-200 bg-white bg-opacity-30 rounded-full text-sm shadow focus:outline-none focus:shadow-outline w-full"
    :placeholder="placeholder"
    style="transition: all 0.15s ease 0s;"
  />
</template>

<style scoped>
button {
  color: #eee;
  text-transform: uppercase;
}
</style>