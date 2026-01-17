<script setup>
import { ref } from "vue";
import Counter from "./Counter.vue";
import CounterStateless from "./CounterStateless.vue";

const counter1 = "Eko";
const counter2 = "Budi";

const counter = ref(0);

</script>

<template>
    <counter :name="counter1" initial-count="10"/>   
    <counter v-bind:name="counter2" initial-count="20"/>
    
    <CounterStateless name="joko" :counter="counter"/>
    <CounterStateless name="Morro" :counter="counter"/>
    <button @click="counter++">Increment Counter</button>
</template>

<style  scoped>

</style>