<template>
  <div class="shema">
    <div class="shema_content">
      <div class="shema_info">
        <a href="#" class="vote" @click.prevent = 'goToVote'>Галасаваць</a>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'shema',
    data () {
      return {

      }
    },

    methods: {
      goToVote() {
        this.$parent.firstPage = true;
        this.$parent.productMobile = false;
        this.$parent.currentMobileNum = 3;
        this.$parent.scrollToMobile();
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/shema.sass'
</style>
