<script setup>
const {title} = defineProps({
    title:String
})

const slots = useSlots(){
    
}
</script>

<template>
   <h1>{{ title }}</h1>
   <div>
        <slot name="header">
            <h1>Default Header</h1>
        </slot>
   </div>
   <div>
        <slot name="default">
            <p>anda belum mengisi kontennya</p>
        </slot>
   </div>
   <div>
        <slot name="footer">
            <p>Default Footer</p>
        </slot>
   </div>
</template>

<style scoped>

</style>