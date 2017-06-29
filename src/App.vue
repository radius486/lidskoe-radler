<template>
  <div id="app">
    <header-component></header-component>
    <attention-popup v-if='attention'></attention-popup>
    <footer-component></footer-component>
  </div>
</template>

<script>
import headerComponent from './components/header-component.vue';
import footerComponent from './components/footer-component.vue';
import attentionPopup from './components/attention-popup.vue';

export default {
  name: 'app',
  data () {
    return {
      attention: true
    }
  },

  components: {
    headerComponent,
    footerComponent,
    attentionPopup
  }
}
</script>

<style lang='sass'>
  html, body
    min-height: 100%
    height: 100%
    margin: 0
    padding: 0

  #app
    width: 100%
    height: 100%
    position: relative
    background-color: #afcb05

</style>
