<template>
  <div class="product">
    <a href="#" @click.prevent='prevSlide' class="prev-slide" :class="{green: currentSlideNum == 2}">Prev</a>
    <a href="#" @click.prevent='nextSlide' class="next-slide" :class="{green: currentSlideNum == 2}">Next</a>
    <div class="slides" :style='{transform: "translateX(" + offset + ")" }'>
      <div class="product_content slide1">
        <div class="product_info"></div>
      </div>
      <div class="product_content slide2">
        <div class="product_info"></div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'product-mobile',
    data () {
      return {
        currentSlideNum: 1
      }
    },

    computed: {
      offset() {
        let height = window.innerWidth;
        return '-' + height * (this.currentSlideNum - 1)  + 'px'
      }
    },

    methods: {
      nextSlide() {
        if (this.currentSlideNum == 1) {
          this.currentSlideNum++;
        }
      },

      prevSlide() {
        if (this.currentSlideNum == 2) {
          this.currentSlideNum--;
        }
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/product-mobile.sass'
</style>
