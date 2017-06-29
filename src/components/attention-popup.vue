<template>
  <div class="attention-popup">
    <div v-if='!restriction' class="attention-popup_inner">
      <p>Вам ужо споўнілася 18 гадоў?</p>
      <div class="attention-popup_actions">
        <button @click='openContent'>Так</button>
        <button @click='showRestriction'>Не</button>
      </div>
    </div>
    <div v-else class="attention-popup_inner restriction">
      <p>Иди нафиг отсюда малолетка.</p>
      <span>Жди когда исполнится 18</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'attention-popup',
  data () {
    return {
      restriction: false
    }
  },

  methods: {
    openContent: function (e) {
      e.preventDefault();
      this.$parent.attention = false;
    },

    showRestriction: function(e) {
      e.preventDefault();
      this.restriction = true;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/attention-popup.sass'
</style>
