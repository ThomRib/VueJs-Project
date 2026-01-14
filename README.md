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

