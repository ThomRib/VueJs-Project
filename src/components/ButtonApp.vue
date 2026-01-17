<script setup>
import MyButton from './MyButton.vue';

function clickHandler(){
    alert("You click me");
}
</script>

<template>
 <MyButton class="button" @click="clickHandler"/>
</template>

<style scoped>
.button{
    display: inline-block;
    padding: 10px 20px;
    background-color: #007bff;
    color: #fff;
    font-size: 16px;
    border: none;
    cursor: pointer;
    text-align: center;
    transition: background-color 0.3s ease, transform 0.2s ease;
}

.button:hover {
    background-color: #0056b3;
    transform: scale(1.05);
}
</style>