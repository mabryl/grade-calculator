<script setup>
import Calculator from './components/Calculator.vue';
import Footer from './components/Footer.vue';
</script>

<template>
  <div class="container">
    <Calculator />
    <Footer />
  </div>
</template>

<style>
* {
  font-family: Lato, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  box-sizing: border-box;
}

html,
body {
  margin: 0;
  padding: 0;
}

.container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

</style>
