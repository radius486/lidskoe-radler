<template>
  <transition name="slide-fade">
    <div class="check-in-popup">
      <button class="close" @click.prevent='closePopup'>Close</button>
      <div id="rega1" class="check-in-popup_left">
        <h2>Рэгістрацыя</h2>
        <p>Колькасць месцаў абмежавана</p>
        <form>
          <input @click.prevent='upd_input("name")' id="name" type="text" placeholder="iмя">
          <input @click.prevent='upd_input("sname")' id="sname" type="text" placeholder="прозвiшча">
          <input @click.prevent='upd_input("phone")' id="phone" type="phone" placeholder="+375 (29) ___ __ __"  v-mask="'+### (##) ##-##-##'"  v-model="myInputModel">
          <input @click.prevent='upd_input("email")' id="email" type="email" placeholder="e-mail:">
          <div class="bookBox">
            <input id="book" value="1" type="checkbox" checked>
            <label for="book">Забранiраваць мне месца на мерапрыемстве</label>
          </div>
        </form>
      </div>
      <div id="rega2" class="check-in-popup_right">
        <div class="image" :class='className'></div>
        <div class="check-in-popup_actions">
          <button @click.prevent='register'>зарэгiстравацца</button>
          <button @click.prevent='closePopup'>адмена</button>
        </div>
      </div>

        <div id="rega3" class="check-in-popup_left" style="display:none; width: 100%;">

          <br><br><br>

          <h2 align="center">Дзякуй!</h2>
          <br>
          <p align="center">Вы паспяхова прайшлі рэгістрацію. Убачымся на вечарыне!</p>

          <br><br>

          <div class="check-in-popup_actions">
            <button @click.prevent='closePopup'>Акей</button>
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

    upd_input(name) {
      document.getElementById(name).style.backgroundColor = '#fff';
      },

    register() {
      console.log('Register to ' + this.className);
      //this.closePopup();

      let name = document.getElementById('name').value;
      let sname = document.getElementById('sname').value;
      let phone = document.getElementById('phone').value;
      let email = document.getElementById('email').value;
      let book = document.getElementById('book').value;

      let err = 0;

      if(!name){document.getElementById('name').style.backgroundColor = '#ffcbcb'; err=1;}
      if(!sname){document.getElementById('sname').style.backgroundColor = '#ffcbcb'; err=1;}
      if(!phone){document.getElementById('phone').style.backgroundColor = '#ffcbcb'; err=1;}
      if(!email){document.getElementById('email').style.backgroundColor = '#ffcbcb'; err=1;}

      if(phone && phone.length<19){
        document.getElementById('phone').style.backgroundColor = '#ffcbcb'; err=1;
        }

      var reg = /^([A-Za-z0-9_\-\.])+\@([A-Za-z0-9_\-\.])+\.([A-Za-z]{2,4})$/;
      if(email && reg.test(email) == false) {
        document.getElementById('email').style.backgroundColor = '#ffcbcb'; err=1;
        }

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

      if(err==0){

        document.getElementById('rega1').style.display='none';
        document.getElementById('rega2').style.display='none';

        document.getElementById('rega3').style.display='block';

        //this.closePopup();
        let client = new HttpClient();
        client.get('https://event.edenkit.com/admin321/save_voite.php?name=' + name + '&sname=' + sname + '&phone=' + phone + '&email=' + email + '&is_going=' + book + '&name_event=' + this.className, function(response) {

          });
        }

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/check-in-popup.sass'
</style>
