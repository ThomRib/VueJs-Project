<script setup>
import { computed, reactive,ref } from 'vue';


const person = reactive({
    firstName: "",
    LastName: ""
})

function sayHello(){
    person.firstName = document.getElementById('firstName').value;
    person.LastName = document.getElementById('LastName').value;
}

// computed digunakan supaya tidak mengeksekusi function bila tidak digunakan
const fullName = computed((oldName) => {
    console.log(`change old name`);
    return `${person.firstName} ${person.LastName}`;
})

const counter = ref(0)

function increment(){
    console.log(`increment called`);
    counter.value++;
}
</script>

<template>
    <div>
        <button v-on:click="increment">Increment {{ counter }}</button> <br>
        <input placeholder="First Name" type="text" id="firstName"> <br>
        <input placeholder="Last Name" type="text" id="LastName"> <br>
        <button v-on:click="sayHello">Say Hello</button>
    </div>
    <h1>Hello{{ fullName}}</h1>
</template>

<style scoped>

</style>