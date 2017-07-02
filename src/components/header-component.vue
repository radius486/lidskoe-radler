<template>
  <div class="header">
    <div class="header-inner">
      <div class="logo">
        <a href="/" title="Галоўная">Галоўная</a>
      </div>
      <div class="header-menu">
        <a href="#" @click.prevent='prevSlide'>Галоўная</a>
        <a href="#" @click.prevent='nextSlide'>Галасаваць</a>
        <a href="#" @click.prevent='goToProduct'>Больш пра ЛIДСКАЕ® Radler</a>
      </div>
      <div class="header-menu_mobile">
        <a href="#" class="open" v-if='!menuOpened' @click.prevent='openMenu'>Open</a>
        <a href="#" class="close" v-else @click.prevent='closeMenu'>Close</a>
        <ul class="header-menu_mobile_inner" v-if='menuOpened'>
          <li><a href="#" @click.prevent='prevSlide'>Галоўная</a></li>
          <li><a href="#" @click.prevent='nextSlide'>Галасаваць</a></li>
          <li><a href="#" @click.prevent='goToProduct'>Больш пра ЛIДСКАЕ® Radler</a></li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'header-component',
  data () {
    return {
      menuOpened: false
    }
  },

  methods: {
    nextSlide() {
      this.$parent.productPage = false;
      if (this.$parent.currentSlideNum == 1) {
        this.$parent.currentSlideNum++;
      }
    },

    prevSlide() {
      this.$parent.productPage = false;
      if (this.$parent.currentSlideNum == 2) {
        this.$parent.currentSlideNum--;
      }
    },

    goToProduct() {
      this.$parent.productPage = true;
    },

    openMenu() {
      this.menuOpened = true;
    },

    closeMenu() {
      this.menuOpened = false;
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/header-component.sass'
</style>
