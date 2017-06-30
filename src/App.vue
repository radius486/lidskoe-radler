<template>
  <div id="app">
    <header-component></header-component>
    <attention-popup></attention-popup>
    <info-popup v-if='!attention' :header='headerFactory' :text='textFactory' :className="'factory'"></info-popup>
<!--<info-popup :header='headerBeach' :text='textBeach' :className="'beach'"></info-popup>
    <info-popup :header='headerBattle' :text='textBattle' :className="'sea-battle'"></info-popup> -->
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
import infoPopup from './components/info-popup.vue';
import view1 from './components/view-1.vue';
import view2 from './components/view-2.vue';
import product from './components/product.vue';

export default {
  name: 'app',
  data () {
    return {
      attention: true,
      currentSlideNum: 1,
      productPage: false,

      headerFactory: 'Арт-вечарына на пляжы',
      textFactory: 'Жадаеш убачыць конкурс муралаў з лепшымі графіцістамі краіны на пляжы, дзе граюць дыджэі? Ты можаш проста танчыць,        сачыць за падзеямі і адпачываць з сябрамі. Гэта свежы фармат «Арт-вечарына на пляжы».'
    }
  },

  components: {
    headerComponent,
    footerComponent,
    attentionPopup,
    infoPopup,
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

  #app
    width: 100%
    height: 100%
    position: relative
    background-color: #afcb05
    overflow: hidden

  .views
    height: 100%
    transition: transform .7s ease-in

  .fade-enter-active, .fade-leave-active
    transition: opacity .5s

  .fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */
    opacity: 0

</style>
