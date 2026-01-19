<script setup>
import { useSlots } from 'vue';

const counter = ref(0);

this.$slots
</script>

<template>
   <div v-if="$slots.header">
        <slot name="header" :counter="counter">
            <h1>Default Header</h1>
        </slot>
   </div>
   <div v-if="$slots.default">
        <slot name="default" :counter="counter">
            <p>anda belum mengisi kontennya</p>
        </slot>
   </div>
   <div v-if="$slots.footer">
        <slot name="footer" :counter="counter">
            <p>Default Footer</p>
        </slot>
   </div>
</template>

<style scoped>

</style>