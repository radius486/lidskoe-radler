<template>
  <transition name="fade">
    <div v-if='opened' class="info-popup_overlay">
      <div class="info-popup">
        <div class="info-popup_inner">
          <button class="close" @click.prevent='closePopup'>Close</button>
          <div class="info-popup_left" :class='className'>
            <div class="info-popup_actions">
              <button>галасаваць</button>
              <button>назад</button>
            </div>
          </div>
          <div class="info-popup_right">
            <h2>{{header}}</h2>
            <p>{{text}}</p>
          </div>
        </div>
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
      opened: true
    }
  },

  methods: {
    closePopup: function() {
      this.opened = false;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/info-popup.sass'
</style>
