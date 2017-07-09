<template>
  <div class="view_item" :class='className'>
    <div class="view_item_inner">
      <h2 class="view_item_title">{{text}}</h2>
      <span class="voice">{{voice}}</span>
    </div>
    <div class="item_overlay">
      <button class="more" @click.prevent='openPopup'>Падрабязней</button>
      <button class="vote" @click.prevent='openCheckIn'>Галасаваць</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'view-item',

    props: ['voice', 'text', 'className'],

    data () {
      return {

      }
    },

    methods: {
      openPopup: function() {
        switch (this.className) {
          case 'factory':
          this.$parent.showFactory = true;
          break;
          case 'beach':
          this.$parent.showBeach = true;
          break;
          case 'sea-battle':
          this.$parent.showBattle = true;
          break;
        }
      },

      openCheckIn: function() {
        switch (this.className) {
          case 'factory':
          this.$parent.checkInFactory = true;
          break;
          case 'beach':
          this.$parent.checkInBeach = true;
          break;
          case 'sea-battle':
          this.$parent.checkInBattle = true;
          break;
        }
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/view-item.sass'
</style>
