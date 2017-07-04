<template>
  <div class="vote">
    <div class="vote_content">
      <h2 class="vote_title">аддай голас<br> за мiкс-вечарыну</h2>
      <div class="vote_list">
        <view-item :voice='voiceFactory' :text='textFactory' :className="'factory'"></view-item>
        <view-item :voice='voiceBeach' :text='textBeach' :className="'beach'"></view-item>
        <view-item :voice='voiceBattle' :text='textBattle' :className="'sea-battle'"></view-item>
      </div>
      <info-popup v-if='showFactory' :header='headerFactory' :text='textFactoryDetailed' :className="'factory'"></info-popup>
      <info-popup v-if='showBeach' :header='headerBeach' :text='textBeachDetailed' :className="'beach'"></info-popup>
      <info-popup v-if='showBattle' :header='headerBattle' :text='textBattleDetailed' :className="'sea-battle'"></info-popup>
      <check-in-popup v-if='checkInFactory' :className="'factory'"></check-in-popup>
      <check-in-popup v-if='checkInBeach' :className="'beach'"></check-in-popup>
      <check-in-popup v-if='checkInBattle' :className="'sea-battle'"></check-in-popup>
    </div>
  </div>
</template>

<script>

  import viewItem from './view-item.vue';
  import infoPopup from './info-popup.vue';
  import checkInPopup from './check-in-popup.vue';

  let count1 = 0;
  let count2 = 0;
  let count3 = 0;

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
  client.get('http://event.edenkit.com/admin321/getstat.php', function(response) {
    let arr_result = response.split(';');
    count1 = arr_result[0];
    count2 = arr_result[1];
    count3 = arr_result[2];
  });

  export default {
    name: 'vote',
    data () {
      return {
        showFactory: false,
        showBeach: false,
        showBattle: false,

        checkInFactory: false,
        checkInBeach: false,
        checkInBattle: false,

        voiceFactory: count1,
        voiceBeach: count2,
        voiceBattle: count3,

        textFactory: 'мазгабойня на заводзе',
        textBeach: 'Арт-вечарына на пляжы',
        textBattle: 'марскi бой у «Дрымлэндзе»',


        headerBeach: 'Арт-вечарына на пляжы',
        textBeachDetailed: 'Жадаеш убачыць конкурс муралаў з лепшымі графіцістамі краіны на пляжы, дзе граюць дыджэі? Ты можаш проста танчыць,        сачыць за падзеямі і адпачываць з сябрамі. Гэта свежы фармат «Арт-вечарына на пляжы».',

        headerFactory: 'мазгабойня на заводзе',
        textFactoryDetailed: 'Жадаеш выпрабаваць свае мазгі ў адным з самых папулярных фарматаў інтэлектуальных гульняў – мазгабойні? Давай зробім гэта ў нечаканым месцы і з вялікай колькасцю людзей, каб атрымалася сапраўдная свежая вечарына. Галасуй за фармат «Мазгабойня на заводзе».',

        headerBattle: 'марскi бой у «Дрымлэндзе»',
        textBattleDetailed: 'Жадаеш прыняць удзел у самай масавай бойцы з водных пісталетаў, правесці час на пляжы ў межах горада і адчуць, што спёка – гэта нагода для прыгод? Аддавай свой голас за свежы фармат вечарыны «Марскі бой у „Дрымлэндзе“». '
      }
    },

    components: {
      viewItem,
      infoPopup,
      checkInPopup
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/vote.sass'
</style>
