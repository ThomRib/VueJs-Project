<script setup>
import { ref } from 'vue';
import Abaut from './Abaut.vue';
import Blog from './Blog.vue';
import Contact from './Contact.vue';

const currentPage = ref('About');
const pages = {
    About,
    Blog,
    Contact
}
</script>

<template>
    <button @click="currentPage = 'About'">About</button>
    <button @click="currentPage = 'Blog'">Blog</button>
    <button @click="currentPage = 'Contact'">Contact</button>

    <component :is="page[currentPage]"/>
</template>

<style scoped>

</style>