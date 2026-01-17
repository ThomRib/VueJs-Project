<script setup>
import { computed, reactive,ref } from 'vue';


const person = reactive({
    firstName: "",
    LastName: ""
})

function sayHello(event){
    person.firstName = document.getElementById('firstName').value;
    person.LastName = document.getElementById('LastName').value;
}

// computed digunakan supaya tidak mengeksekusi function bila tidak digunakan
const fullName = computed((oldName) => {
    console.log(`change old name`);
    return `${person.firstName} ${person.LastName}`;
})

const counter = ref(0)

function changeFirstName(event){
    person.firstName = event.target.value;
}

function changeLastName(event){
    person.LastName = event.target.value;
}

</script>

<template>
    <div>
        <button v-on:click="counter++">Increment {{ counter }}</button> <br>
        <input placeholder="First Name" type="text" id="firstName" v-on:input="changeFirstName"> <br>
        <input placeholder="Last Name" type="text" id="LastName" @input="changeLastName"> <br>
        <button v-on:click.prevent="sayHello">Say Hello</button>
    </div>
    <h1>Hello{{ fullName}}</h1>
</template>

<style scoped>

</style>