<script setup lang="ts">
import { reactive, toRefs } from "vue";

type Prop = {
    text: String;
    type?: "button"| "submit" | "reset";
    size: String;
    variant: "primary" | "secondary" | 'tertiary';
    disable: true | false;
}

const props = withDefaults(defineProps<Prop>(), {
    variant: 'primary',
    disable: false
})


const { size, variant, disable, text, type: typeButton, } = toRefs(props)

const style = reactive({
    'bg-blue-500 hover:bg-blue-400 text-white': variant.value === 'primary',
    'bg-red-500 hover:bg-red-400 text-white': variant.value === 'secondary',
    'bg-transparent hover:text-gray-200 text-gray-500': variant.value === 'tertiary',
})
</script>

<template>
    <button
        class="py-3 outline-none "
        :class="style"
        :type="typeButton"
    >{{ text }}</button>
</template>

<style>
</style>