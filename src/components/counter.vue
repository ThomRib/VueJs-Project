<script setup>
    let count = 0;

    function increment(){
        console.info(`Increment counter : ${count}`);
        count++;

        document.getElementById("count").innerText =
    }
</script>

<template>
    <div>
        <h1 id="count">Counter : {{ count }}</h1>
        <button v-on:click="increment">Increment</button>
    </div>
</template>

<style scoped>
 
</style>