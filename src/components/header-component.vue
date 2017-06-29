<template>
  <div class="header">
    <div class="header-inner">
      <div class="logo">
        <a href="/" title="Галоўная">Галоўная</a>
      </div>
      <div class="header-menu">
        <a href="#">Галоўная</a>
        <a href="#" @click.prevent='nextSlide'>Галасаваць</a>
        <a href="#">Больш пра ЛIДСКАЕ® Radler</a>
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
      if (this.$parent.currentSlideNum < 2) {
        this.$parent.currentSlideNum++;
      }
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/header-component.sass'
</style>
