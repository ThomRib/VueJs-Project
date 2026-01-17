<script setup>
    const props = defineProps(["class"])
    const emits = defineEmits(["click"])
</script>

<template>
    <button :class="props.class" @click="emits('click')">My Button</button>
</template>

<style scoped>

</style>