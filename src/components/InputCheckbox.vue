<script setup lang="ts">
import { toRefs } from 'vue'

const props = defineProps({
  text: { type: String },
});

const { text } = toRefs (props)

</script>

<template>
    <label class="inline-flex items-center cursor-pointer">
        <input
            id="customCheckLogin"
            type="checkbox"
            class="form-checkbox accent-blue-600 focus:outline-none w-4 h-4"
            style="transition: all 0.15s ease 0s;"
        />
        <span class="ml-2 text-sm font-semibold text-gray-200">{{ text }}</span>
    </label>
</template>

<style>
</style>