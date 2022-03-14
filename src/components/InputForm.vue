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

</script>

<template>
  <label
    class="block uppercase text-gray-700 text-xs font-light mb-2"
    for="grid-password"
  >{{ label }}</label>
  <input
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
    :type="type"
    class="px-3 py-3 placeholder-gray-400 text-gray-700 bg-white rounded-full text-sm shadow focus:outline-none focus:shadow-outline w-full"
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