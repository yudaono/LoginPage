<script setup lang="ts">
import { ref } from "vue";

const props = defineProps({
  text: { type: String },
});
</script>

<template>
  <button
    class="text-gray-800 py-2 mr-4 mb-1 uppercase underline underline-offset-8 inline-flex items-center font-normal text-xs"
  >{{ text }}</button>
</template>
  
<style scoped>
</style>
