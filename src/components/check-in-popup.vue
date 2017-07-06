<template>
  <transition name="fade">
    <div class="check-in-popup">
      <button class="close" @click.prevent='closePopup'>Close</button>
      <div class="check-in-popup_left">
        <h2>Рэгістрацыя</h2>
        <p>Колькасць месцаў абмежавана</p>
        <form>
          <input id="name" type="text" placeholder="iмя">
          <input id="sname" type="text" placeholder="прозвiшча">
          <input id="phone" type="phone" placeholder="+375 (29) ___ __ __"  v-mask="'+375 (##)-###-##-##'"  v-model="myInputModel">
          <input id="email" type="email" placeholder="e-mail:">
          <div class="bookBox">
            <input id="book" value="1" type="checkbox">
            <label for="book">Забранiраваць мне месца на мерапрыемстве</label>
          </div>
        </form>
      </div>
      <div class="check-in-popup_right">
        <div class="image" :class='className'></div>
        <div class="check-in-popup_actions">
          <button @click.prevent='register'>зарэгiстравацца</button>
          <button @click.prevent='closePopup'>адмена</button>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
import Vue     from 'vue';
import VueMask from 'v-mask';

Vue.use(VueMask);

export default {
  name: 'check-in-popup',

  props: ['className'],

  data () {
    return {
      myInputModel: null
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
      console.log('Register to ' + this.className);
      this.closePopup();

      let name = document.getElementById('name').value;
      let sname = document.getElementById('sname').value;
      let phone = document.getElementById('phone').value;
      let email = document.getElementById('email').value;
      let book = document.getElementById('book').value;

      let HttpClient = function() {
        this.get = function(aUrl, aCallback) {
          let anHttpRequest = new XMLHttpRequest();
          anHttpRequest.onreadystatechange = function() {
            if (anHttpRequest.readyState == 4 && anHttpRequest.status == 200)
              aCallback(anHttpRequest.responseText);
          }
          anHttpRequest.open( "GET", aUrl, true );
          anHttpRequest.send( null );
        }
      }

      let client = new HttpClient();
      client.get('http://event.edenkit.com/admin321/save_voite.php?name=' + name + '&sname=' + sname + '&phone=' + phone + '&email=' + email + '&is_going=' + book + '&name_event=' + this.className, function(response) {

      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/check-in-popup.sass'
</style>
