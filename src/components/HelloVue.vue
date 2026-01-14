<!-- script setup 
    sebagai penanda vue melakukan transformasi 
    sehingga membolehkan kita 
    menggunakan composition API 
-->

<!-- script 1 -->
<script setup>
    console.info("Hello Vue");

    const hello = "<h1>Hello Vue</h1>"
    const classHello="hello"
    const id ="hello";
    const buttonDisabled = false;
</script>

<!-- template 2 -->
<template>
    <h1 :id v-bind:class="classHello">{{hello}}</h1>
    <!-- v-html adalah dairektif html -->
    <div :class="classHello" v-html="hello"></div>
    <button :disabled>this is button</button>
</template>

<!-- style 3 -->
<style scoped>
    .Hello{
        color: green;
    }
</style>