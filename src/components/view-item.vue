<template>
  <div class="view_item" :class='className'>
    <h2 class="view_item_title">{{text}}</h2>
    <span class="voice">{{voice}}</span>
    <div class="item_overlay">
      <button class="more" @click.prevent='openPopup'>Падрабязней</button>
      <button class="vote">Галасаваць</button>
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
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/view-item.sass'
</style>
