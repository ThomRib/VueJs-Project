<script setup>
import { provide, reactive } from 'vue';
import Profile from './Profile.vue';
import ProfileAddress from './ProfileAddress.vue';

const profile = reactive({
    name: "Admin",
    email: "admin@gmail.com"
})

provide("profile", profile);
</script>

<template>
    <input v-model="profile.name" type="text" placeholder="Name">
    <Profile/>
    <ProfileAddress/>
</template>

<style scoped>

</style>