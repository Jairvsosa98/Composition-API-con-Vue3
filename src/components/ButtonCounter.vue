<script setup>
import { ref } from 'vue';

const counter = ref(0)
const increment = () => {
    counter.value++
}
const decrement = () => {
    if(counter.value <= 0){
        counter.value = 0
    }else {
        counter.value--
    }
}
</script>

<template>
    <button @click.middle="decrement" @click="increment" >Counter {{counter}}</button>
</template>

<style>
</style>