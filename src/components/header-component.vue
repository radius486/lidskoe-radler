<template>
  <div class="header">
    <div class="header-inner">
      <div class="logo">
        <a href="/" title="Галоўная"></a>
      </div>
      <div class="header-menu">
        <a href="#" @click.prevent='prevSlide'>Галоўная</a>
        <a href="#" @click.prevent='nextSlide'>Галасаваць</a>
        <a href="#" @click.prevent='goToProduct'>Больш пра ЛIДСКАЕ® Radler</a>
      </div>
      <div class="header-menu_mobile">
        <transition name='open-menu'>
          <ul class="header-menu_mobile_inner" v-if='$parent.menuOpened'>
            <li><a href="#" @click.prevent='goToShema'>Як удзельнiчаць</a></li>
            <li><a href="#" @click.prevent='goToVote'>Галасаваць</a></li>
            <li><a href="#" @click.prevent='goToProductMobile'>Больш пра ЛIДСКАЕ® Radler</a></li>
          </ul>
        </transition>
        <a href="#" class="open" v-if='!$parent.menuOpened' @click.prevent='openMenu'>Open</a>
        <a href="#" class="close" v-else @click.prevent='closeMenu'>Close</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'header-component',
  data () {
    return {

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

    goToShema() {
      this.closeMenu();
      this.$parent.shemaPage = true;
      this.$parent.homePage = false;
      this.$parent.productMobile = false;
      this.$parent.votePage = false;
    },

    goToVote() {
      this.closeMenu();
      this.$parent.votePage = true;
      this.$parent.shemaPage = false;
      this.$parent.homePage = false;
      this.$parent.productMobile = false;
    },

    goToProductMobile() {
      this.closeMenu();
      this.$parent.homePage = false;
      this.$parent.shemaPage = false;
      this.$parent.productMobile = true;
      this.$parent.votePage = false;
    },

    openMenu() {
      this.$parent.menuOpened = true;
    },

    closeMenu() {
      this.$parent.menuOpened = false;
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/header-component.sass'
</style>
