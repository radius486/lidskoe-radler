<template>
  <transition name="fade">
    <div class="info-popup">
      <button class="close" @click.prevent='closePopup'>Close</button>
      <div class="info-popup_left">
        <div class="image" :class='className'></div>
        <div class="info-popup_actions">
          <button @click.prevent='openCheckIn'>галасаваць</button>
          <button @click.prevent='closePopup'>назад</button>
        </div>
      </div>
      <div class="info-popup_right">
        <h2>{{header}}</h2>
        <p>{{text}}</p>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'info-popup',

  props: ['header', 'text', 'className'],

  data () {
    return {

    }
  },

  methods: {
    closePopup: function() {
      switch (this.className) {
        case 'factory':
        this.$parent.showFactory = false;
        break;
        case 'beach':
        this.$parent.showBeach = false;
        break;
        case 'sea-battle':
        this.$parent.showBattle = false;
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

      this.closePopup();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/info-popup.sass'
</style>
