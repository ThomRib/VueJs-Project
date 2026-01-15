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

# Reactive State
Pada kode sebelumnya, kita mengubah counter secara manual menggunakan manipulasi DOM. Sebenarnya hal ini tidak direkomenadiskan lagi jika menggunakan Vue</br>
Vue menyediakan fitur bernama Reactive State, fungsinya sama untuk menyimpan State (data)</br>
Yang membedakan dengan kita membuat variable sendiri adalah, saat kita mengubah State, maka Vue akan melakukan render ulang Component nya, sehingga Component akan ditampilkan ulang dengan data State yang baru yang sudah kita ubah</br>
Untuk membuat Reactive State, kita bisa menggunakan function ref()</br>
https://vuejs.org/api/reactivity-core.html#ref

---

# Kenapa Reactive State?
Kita harus menggunakan reff dibanding lakukan secara manual?</br>
Ketiak di Template menggunakan ref, lalu kita mengubah value di ref. Vue secara otomatis mendeteksi perubahannya, dan kemudian mengupdate DOM</br>
Vue menggunakan object dengan attribut value sebagai State, agar bisa meng-intercept perubahan data dari get dan set operations, sehingga dengan mudah Vue bisa mendeteksi State mana yang berubah, dan melakukan render ulang Component tersebut di DOM</br>
https://javascript.info/property-accessors

---

# DOM Update
Saat kita mengubah State di Vue, Vue tidak melakukan render saat itu juga</br>
Vue memiliki jadwal untuk melakukan render, hal ini agar jika terjadi perubahan banyak State dalam waktu waktu, Vue bisa menunggu dulu sampai semua perubahan State selesai, baru melakukan render ulang</br>
Jadwal Vue melakukan render ulang selanjutnya kita sebut dengan "next tick"</br>
Jika misal kita ingin melakukan sesuatu setelah proses render ulang selanjutnya selesai, kita bisa menunggunya dengan cara memanggil function nextTick()</br>
https://vuejs.org/api/general.html#nexttick

---

# Reactive
Selain membuat Reactive State menggunakan ref(). kita juga membuat Reactive State menggunakan reactive()</br>
https://vuejs.org/api/reactivity-core.html#reactive</br>
Namun, penggunaan reactive() ini digunakan untuk tipe data complex, karena hasil dari reactive() ini adalah JavaScript Proxies, dimana tiap perubahan ke data nya akan dideteksi oleh Vue, sehingga Vue bisa melakukan render ulang Component setelah mendeteksi perubahan</br>
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy

---

# Keterbatasan Reactive
Saat kita menggunakan reactive() terdapat beberapa keterbatasan dibanding ref()</br>
Karena menggunakan JavaScript Proxy, jadi hanya tipe data objects(object, array, collection) yang bisa digunakan, tidak bisa untuk tipe data primitive(string, number, boolean)</br>
Tidak bisa di replace seluruh object nya, karena akan menjadikan Proxy diubah dengan object baru, sehingga Vue akan kehilangan kemampuan untuk melakukan track perubahan data</br>
Tidak aman saat menggunakan Destructuring Object, karena saat kita melakukan Destructuring Object, secara otomatis hasil Destructuring tersebut keluar dari JavaScript Proxy

---

# Masalah Dengan Method
Sampai saat ini, mungkin kita tidak melihat ada masalah.</br>
Tapi sebenarnya ada masalah yang terjadi ketika kita membuat method / function </br>
Masalahnya adalah, setiap Component di render-ulang, maka method/function tersebut akan dipanggil lagi, walaupun tidak ada state yang berubah</br>
Jika method / function sebenarnya mengembalikan value yang sama, dikarenakan State nya tetap sama, maka alangkah lebih baiknya kita tidak perlu mengeksekusi ulang logic dari method nya

---

# Compute Properties
Masalah ini sudah disediakan solusinya oleh Vue, yaitu menggunakan computed() function</br>
https://vuejs.org/api/reactivity-core.html#computed</br>
Vue bisa tahu isi State yang digunakan di dalam computed() function, dan ketika terjadi perubahan di State tersebut, maka function di computed() akan dipanggil ulang</br>
Jika tidak ada State yang berubah, maka function di computed() tidak akan dipanggil ulang(atau di Cache)</br>
Return value dari computed() mirip seperti ref(), yaitu object {value}

---

# Style
Salah satu yang bisa dilakukan saat membuat Component adalah menambahkan Style </br>
Saat menambahkan Style, kita bisanya menggunakan attribute class atau style, dan karena itu adalah attribute, kita bisa menggunakan Directive v-bind jika butuh value JavaScript Expression</br>
Salah satu hal menari di Vue adalah, saat v-bind menggunakan argument class atau style, value nya bisa menggunakan Object dan Array

---

# Binding HTML Class
Saat menggunakan v-bind:class, kita bisa menggunakan object, dimana jika value object bernilai true, secara otomatis attribute akan dijadikan class nya</br>
Selain object, kita juga bisa menggunakan array

---

# Binding Inline Style
Selain menggunakan attribute class, kita juga bisa menggunakan attribute style jika ingin membuat inline style</br>
Sama seperti class, v-bind:style juga mendukung value Object atau Array</br>
Berbeda dengan style yang menggunakan value boolean pada Object-nya, pada style, kita harus menyebutkan value CSS nya</br>
Dan untuk Array, digunakan untuk menggabungkan beberapa Object style

---