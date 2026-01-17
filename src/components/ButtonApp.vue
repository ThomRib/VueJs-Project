<script setup>
import MyButton from './MyButton.vue';
import Container from './Container.vue';

function clickHandler(){
    alert("You click me");
}
</script>

<template>
 <container title="Contoh Button">
    <template #header="attributes">
        <h1>Button App{{ attributes.counter }}</h1>
    </template>

    <template v-slot:default="attributes">
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptate at dolorem ipsa eos quas maxime atque. Cum voluptates, exercitationem sapiente enim nobis repellat eaque minima ad! Doloremque pariatur eum saepe.</p>
        <MyButton class="button" @click="clickHandler" :name="attributes.counter" contoh="kurniawan"/>
    </template>

    <template #footer>
        <p>Copyright 2024 @Program 2026</p>
    </template>
 </container>
 
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