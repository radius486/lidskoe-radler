<template>
  <div class="header">
    <div class="header-inner">
      <div class="logo">
        <a href="http://lidskae.by" title="Лідскае піва"></a>
      </div>
      <div class="header-menu">
        <a href="#" @click.prevent='prevSlide' :class="{ active: $parent.currentSlideNum == 1 && !$parent.productPage}">Галоўная</a>
        <a href="#" @click.prevent='nextSlide' :class="{ active: $parent.currentSlideNum == 2 && !$parent.productPage}">Галасаваць</a>
        <a href="#" @click.prevent='goToProduct' :class="{ active: $parent.productPage}">Больш пра ЛIДСКАЕ® Radler</a>
      </div>
      <div class="header-menu_mobile">
        <transition name='open-menu'>
          <ul class="header-menu_mobile_inner" v-if='$parent.menuOpened'>
            <li :class="{ active: $parent.currentMobileNum == 2 && !$parent.productMobile}"><a href="#" @click.prevent='goToShema'>Як удзельнiчаць</a></li>
            <li :class="{ active: $parent.currentMobileNum == 3 && !$parent.productMobile}"><a href="#" @click.prevent='goToVote'>Галасаваць</a></li>
            <li :class="{ active: $parent.productMobile}"><a href="#" @click.prevent='goToProductMobile'>Больш пра ЛIДСКАЕ® Radler</a></li>
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
      this.$parent.firstPage = true;
      this.$parent.productMobile = false;
      this.$parent.currentMobileNum = 2;
      this.$parent.scrollToMobile();
    },

    goToVote() {
      this.closeMenu();
      this.$parent.firstPage = true;
      this.$parent.productMobile = false;
      this.$parent.currentMobileNum = 3;
      this.$parent.scrollToMobile();
    },

    goToProductMobile() {
      this.closeMenu();
      this.$parent.firstPage = false;
      this.$parent.productMobile = true;
      this.$parent.currentMobileNum = 1;
      this.$parent.scrollToMobile();
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
