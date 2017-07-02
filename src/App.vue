<template>
  <div id="app">
    <div class="lemons" v-bind:class="{ animate: currentSlideNum == 2, 'is-visiable': !attention}"></div>
    <header-component></header-component>
    <attention-popup></attention-popup>
    <transition name="fade">
      <div  @wheel='onScroll' class="views" v-if='!attention && !productPage' :style='{transform: "translateY(" + offset + ")" }'>
        <view-1></view-1>
        <view-2></view-2>
      </div>
    </transition>
    <transition name="fade">
      <product v-if='productPage'></product>
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
import product from './components/product.vue';

export default {
  name: 'app',
  data () {
    return {
      attention: true,
      currentSlideNum: 1,
      productPage: false
    }
  },

  components: {
    headerComponent,
    footerComponent,
    attentionPopup,
    view1,
    view2,
    product
  },

  computed: {
    offset() {
      let height = window.innerHeight;
      return '-' + height * (this.currentSlideNum - 1)  + 'px'
    }
  },

  methods: {
    onScroll: function(e) {
      e.preventDefault()
      e.stopPropagation();
      let delta = e.deltaY;
      if (delta > 0) {
        this.currentSlideNum = 2;
      } else {
        this.currentSlideNum = 1;
      }
    }
  }
}
</script>

<style lang='sass'>
  @font-face
    font-family: "futurafuturiscbold"
    src: url('assets/fonts/futurafuturiscbold.otf')

  @font-face
    font-family: "futurafuturis"
    src: url('assets/fonts/futurafuturis.otf')

  html, body
    min-height: 100%
    height: 100%
    margin: 0
    padding: 0
    font-family: 'futurafuturiscbold'
    background-color: #afcb05

  #app
    width: 100%
    height: 100%
    position: relative
    overflow: hidden
    background-size: contain

  .lemons
    content: ''
    position: absolute
    display: block
    top: 0
    bottom: 0
    left: 0
    right: 0
    background: url('assets/images/left-lemons.png') repeat-y left center, url('assets/images/right-lemons.png') repeat-y right center
    transition: background 0.7s ease-in, opacity 0.5s ease-in
    opacity: 0

    &.is-visiable
      opacity: 1

    &.animate
      background-position-y: -300px

  .views
    height: 100%
    transition: transform .7s ease-in

  .fade-enter-active, .fade-leave-active
    transition: opacity .5s

  .fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */
    opacity: 0

</style>
