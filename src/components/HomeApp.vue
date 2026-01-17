<script setup>
import { ref } from 'vue';
import Abaut from './Abaut.vue';
import Blog from './Blog.vue';
import Contact from './Contact.vue';

const currentPage = ref('about');

const pages ={
    about: About,
    blog: Blog,
    Contact: Contact
}
</script>

<template>
    <button @click="currentPage ='about'">About</button>
    <button @click="currentPage ='blog'">Blog</button>
    <button @click="currentPage ='contact'">Contact</button>
    <component :is="pages[currentPage]"/>
</template>

<style scoped>

</style>