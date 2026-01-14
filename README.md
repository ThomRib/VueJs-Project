# Vue 3 + Vite

---

# Proses Install
## install vue project
```git
    npm create vit@latest VueJs-Project -- --template vue
```

## menjalankan vue project
```git
    npm run dev
```

---

## Contoh Single File Component
```vue
    <template>
    <!-- HTML template -->
    </template>

    <script>
    // JavaScript logic
    </script>

    <style>
    /* CSS styling */
    </style>
```

# API Style
## Contoh dengan Option API
```vue
    <script>
    export default {
        data(){
            return{
                count: 0
            }
        }
    },
    methods:{
        increment(){
            this.count++
        }
    },
    mounted(){
        console.log('The initial count is ${this.count}.')
    }
    </script>
    <template>
        <button @click="increment">Count is: {{count}}</button>
    </template>
```

## Contoh dengan Composition API
```vue
    <script setup>

        import { ref, onMounted } from 'vue'

        const count = ref(0)

        function increment = () {
            count.value++
        }

        onMounted(() => {
            console.log(`The intial count is ${count.value}.`)
        })
    </script>

    <template>
        <button @click="increment">count is : {{count}}</button>
    </template>
```

---

# Template
perintah directive v-bind:nama-attribute
```vue
    v-bind:class
    :id
    :class
    v-html
```

---

# Boolean Attribute
penggunaan biasanya pada kasus disabled dan check

---

# Multiple Attributes
Directive v-bind juga mendukung mengubah beberapa attribut sekaligus menggunakan JavaScript Object</br>
Kita hanya perlu siapkan data object yang berisi field nama attribute nya
```vue
    <script>
        const hello = "<h1>Hello Vue</h1>"
        const buttonDisabled = true;
        const data = {
            id: "hello",
            class: "hello",
        }
    </script>
    <template>
        <h1 v-bind="data">{{hello}}</h1>
        <div :class="data.class" v-html="hello"></div>
        <button :disabled="buttonDisabled">This is Button</button>
    </template>
```

---

# JavaScript Expression di Template
JavaScript Expression adalah kode yang menghasilkan nilai, dari mulai variable sampai memanggil function
```vue
    <script>
       function hellofunction(){
        return "Hello world";
       }
    </script>
    <template>
       <h2>{{ 100 * 200}}</h2> 
       <h2>{{hellofunction}}</h2>
    </template>
```

---

# Directive Arguments
Beberapa jenis Directive, bisa memiliki Arguments</br>
Directive Argument ditandai dengan tanda : (titik dua) setelah Directive nya</br>
href pada v-bind adalah Argument</br>
Selain v-bind, ada juga seperti contohnya Directive v-on:click

---

# Dynamic Arguments
Directive juga mendukung Dynamic Arguments, yang artinya nama Argument bisa menggunakan JavaScript Expression</br>
Untuk menggunakan Dynamic Argument, kita bisa gunakan [] kurung kotak, dimana didalam kurung kotaknya, kita bisa tambahkan JavaScript Expression</br>
Misa kita bisa gunakan v-bind[fromVariable], diamna misal fromVariable adalah variable dari kode JavaScript</br>
Ekspektasi value dari Dynamic Argument adalah String, namun selain String, kita juga bisa gunakan null, jika nilai dari Dynamic Argument adalah null, artinya kita ingin menghapus Argument tersebut

---

# Modifier
Modifier adalah suffix (akhiran) yang terdapat di Directive yang diawali dengan karakter. (titik)</br>
Beberapa Directive memiliki Modifier, contohnya adalah Directive v-on, misal </br>
v-on:submit.prevent="onSubmit"</br>
v-on adalah Directive</br>
Submit adalah Attribute</br>
Prevent adalah Modifire</br>
"onSubmit" adalah value

---

# State
Saat kita membuat halaman web, kita mungkin akan menyimpan data (state) di JavaScript</br>
Misal,ketika kita membuat halaman untuk menampilkan data Counter berapa banyak pengguna mengklik tombol, kita bisa menyimpan state (data saat ini) di JavaScript

---


