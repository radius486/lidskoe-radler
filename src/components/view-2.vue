<template>
  <div class="view-2">
    <div class="view_inner">
      <h2 class="view_title">аддай голас<br> за мiкс-вечарыну</h2>
      <h3 class="view_subtitle">і атрымай магчымасць выйграць квіткі</h3>
      <div class="view_list">
        <view-item :voice='voiceFactory' :text='textFactory' :className="'factory'"></view-item>
        <view-item :voice='voiceBeach' :text='textBeach' :className="'beach'"></view-item>
        <view-item :voice='voiceBattle' :text='textBattle' :className="'sea-battle'"></view-item>
      </div>
    </div>
  </div>
</template>

<script>

  import viewItem from './view-item.vue';

  export default {
    name: 'view-2',
    data () {
      return {
        voiceFactory: 250,
        voiceBeach: 468,
        voiceBattle: 127,
        textFactory: 'мазгабойня на заводзе',
        textBeach: 'Арт-вечарына на пляжы',
        textBattle: 'марскi бой у «Дрымлэндзе»'
      }
    },

    components: {
      viewItem
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/view-2.sass'
</style>
