<script setup>
import { useSlots } from 'vue';
const slots = useSlots();

</script>

<template>
   <div v-if="slots.header">
        <slot name="header">
            <h1>Default Header</h1>
        </slot>
   </div>
   <div v-if="slots.default">
        <slot name="default">
            <p>anda belum mengisi kontennya</p>
        </slot>
   </div>
   <div v-if="slots.footer">
        <slot name="footer">
            <p>Default Footer</p>
        </slot>
   </div>
</template>

<style scoped>

</style>