<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps ({
  text : { type: String }
})
</script>

<template>
  <button class="bg-white active:bg-gray-100 text-gray-800 font-normal px-4 py-2 rounded outline-none focus:outline-none mr-2 mb-1 uppercase shadow hover:shadow-md inline-flex items-center font-bold text-xs">{{ text }}</button>
</template>
  
<style scoped>

</style>
