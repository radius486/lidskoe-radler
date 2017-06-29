<template>
  <div id="app">
    <header-component></header-component>
    <footer-component></footer-component>
  </div>
</template>

<script>
import headerComponent from './components/header-component.vue';
import footerComponent from './components/footer-component.vue';

export default {
  name: 'app',
  components: {
    headerComponent,
    footerComponent
  }
}
</script>

<style>
  html, body {
    min-height: 100%;
    height: 100%;
    margin: 0;
    padding: 0;
  }
  #app {
    width: 100%;
    height: 100%;
    position: relative;
    background-color: #afcb05;
  }
</style>
