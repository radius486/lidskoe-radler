<template>
  <div id="app">
    <header-component></header-component>
    <attention-popup></attention-popup>
    <transition name="fade">
      <div class="views" v-if='!attention' :style='{transform: "translateY(" + offset + ")" }'>
        <view-1></view-1>
        <view-2></view-2>
      </div>
    </transition>
    <footer-component></footer-component>
  </div>
</template>

<script>
import headerComponent from './components/header-component.vue';
import footerComponent from './components/footer-component.vue';
import attentionPopup from './components/attention-popup.vue';
import view1 from './components/view-1.vue';
import view2 from './components/view-2.vue';

export default {
  name: 'app',
  data () {
    return {
      attention: true,
      currentSlideNum: 1
    }
  },

  components: {
    headerComponent,
    footerComponent,
    attentionPopup,
    view1,
    view2
  },

  computed: {
    offset() {
      let height = window.innerHeight;
      return '-' + height * (this.currentSlideNum - 1)  + 'px'
    }
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
    overflow: hidden

  .views
    height: 100%
    transition: transform .5s ease-in

  .fade-enter-active, .fade-leave-active
    transition: opacity .5s

  .fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */
    opacity: 0

</style>
