<script setup>
import { ref } from 'vue';
import Header from './components/header.vue';

</script>

<template>

  <h1>나의 Vue과제방</h1>
    <Header />


</template>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
h1 {
  margin-left: 200px;
  padding: 20px;
  display: flex;
  justify-content: center;
  /* 가로 중앙 */
  align-items: center;
  /* 세로 중앙 */
  height: 100px;
  font-size: clamp(1.5rem, 5vw, 3rem);
}

</style>
