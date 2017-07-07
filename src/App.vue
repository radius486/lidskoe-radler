<template>
  <div id="app" @mousemove='goParallax' :class="{ 'mobile-scrolling': !attention && !productMobile}">
    <div class="lemons" :class="{ animate: currentSlideNum == 2, 'is-visiable': !attention}" :style='{marginLeft: parallaxPosition}'></div>
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

    <div class="mobile-layout" @click='menuOpened = false'>
      <div class="first-page" v-if='firstPage && !attention'>
        <home></home>
        <shema></shema>
        <vote></vote>
      </div>

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
      currentMobileNum: 1,
      productPage: false,
      productMobile: false,
      firstPage: true,
      menuOpened: false,
      parallaxPosition: 0
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
      return '-' + height * (this.currentSlideNum - 1)  + 'px';
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
    },

    goParallax(e) {
      let position = - e.clientX/200 + 'px';
      this.parallaxPosition = position;
    },

    scrollToMobile() {
      let height = window.innerHeight;
      let coord = height * (this.currentMobileNum - 1);
      document.getElementById('app').scrollTop = coord;
      console.log(coord);
    }
  }
}
</script>

<style lang='sass'>
  @import './assets/styles/app.sass'
</style>
