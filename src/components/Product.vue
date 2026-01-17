<script setup>
import { onWatcherCleanup, ref, watch, watchEffect } from 'vue';

const productId = ref("product1");
const product = ref(null);

// menggunakan watch
// watch(productId,async(newVal, oldVal) => {
    
//     console.log(`call watch callback`);
//     const response = await fetch(`/${newVal}.json`);
//     product.value =await response.json();
// }, {
//         immediate: true
// })

// menggunakan watchEffect
watchEffect(async (newVal, oldVal) => {
    // onwatchercleanup
    onWatcherCleanup(() => {
        console.log("clean up");
    })

    console.log(`call watch callback`);
    const response = await fetch(`/${productId.value}.json`);
    product.value = await response.json();
})
</script>

<template>
<label for="productId">
    product Id :
    <select v-model="productId">
        <option value=""></option>
        <option value="product1">Product 1</option>
        <option value="product2">Product 2</option>
        <option value="product3">Product 3</option>
    </select>
</label>
<div v-if="product">
    <productDetail :id="product.id" :price="product.price" :name="product.name"/>
    <!-- <h1>Product</h1>
    <p>Id : {{ product.id }}</p>
    <p>Id : {{ product.name }}</p>
    <p>Id : {{ product.price }}</p> -->
</div>
</template>

<style scoped>

</style>