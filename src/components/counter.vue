<script setup>
    let count = 0;

    function increment(){
        count++;
    }
</script>

<template>
    <div>
        <h1>Counter : {{ count }}</h1>
        <button v-on:click="increment">Increment</button>
    </div>
</template>

<style scoped>
 
</style>