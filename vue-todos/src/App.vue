<script setup>
import { RouterView } from 'vue-router'
import TodoHeader from './components/TodoHeader.vue';

</script>

<template>
  <TodoHeader/>
  <RouterView />
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;500;700&display=swap");


* {
  font-family: "Rubik", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
}

body {
  background: #dd3e54;
  /* fallback for old browsers */
  background: -webkit-linear-gradient(to right, #6be585, #dd3e54);
  /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(to right, #6be585, #dd3e54);
  /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}
</style>
