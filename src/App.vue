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

    <div class="mobile-layout">
      <transition name="fade">
        <home v-if='homePage && !attention'></home>
      </transition>

      <transition name="fade">
        <shema v-if='shemaPage'></shema>
      </transition>

      <transition name="fade">
        <vote v-if='votePage'></vote>
      </transition>

      <transition name="fade">
        <product-mobile v-if='productMobile'></product-mobile>
      </transition>
    </div>
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
import productMobile from './components/product-mobile.vue';
import shema from './components/shema.vue';
import home from './components/home.vue';
import vote from './components/vote.vue';

export default {
  name: 'app',
  data () {
    return {
      attention: true,
      currentSlideNum: 1,
      productPage: false,
      productMobile: false,
      shemaPage: false,
      homePage: true,
      votePage: false
    }
  },

  components: {
    headerComponent,
    footerComponent,
    attentionPopup,
    view1,
    view2,
    product,
    productMobile,
    shema,
    home,
    vote
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
  @import './assets/styles/app.sass'
</style>
