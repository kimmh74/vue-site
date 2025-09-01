<script setup>
import {ref} from 'vue';

const count = ref(0)
function increment(){
    count.value++
}

</script>

<template>
    <h1>안녕 Vue야~~~!!!!</h1>
<!-- <button @click="increment">숫자세기 : {{count}}</button> -->

</template>
