<template>
  <transition name="fade">
    <div class="check-in-popup_overlay">
      <div class="check-in-popup">
        <div class="check-in-popup_inner">
          <button class="close" @click.prevent='closePopup'>Close</button>
          <div class="check-in-popup_left">
            <h2>Рэгістрацыя</h2>
            <p>Колькасць месцаў абмежаван</p>
            <form>
              <input type="text" placeholder="iмя">
              <input type="text" placeholder="прозвiшча">
              <input type="phone" placeholder="+375 (29) ___ __ __">
              <input type="email" placeholder="e-mail:">
              <div class="bookBox">
                <input id="book" type="checkbox">
                <label for="book">Забранiраваць мне месца на мерапрыемстве</label>
              </div>
            </form>
          </div>
          <div class="check-in-popup_right" :class='className'>
            <div class="check-in-popup_actions">
              <button @click.prevent='register'>зарэгiстравацца</button>
              <button @click.prevent='closePopup'>адмена</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'check-in-popup',

  props: ['className'],

  data () {
    return {

    }
  },

  methods: {
    closePopup: function() {
      switch (this.className) {
        case 'factory':
        this.$parent.checkInFactory = false;
        break;
        case 'beach':
        this.$parent.checkInBeach = false;
        break;
        case 'sea-battle':
        this.$parent.checkInBattle = false;
        break;
      }
    },

    register() {
      //TODO: Add registration here
      console.log('Register to ' + this.className);
      this.closePopup();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/check-in-popup.sass'
</style>
