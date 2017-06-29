<template>
  <div class="attention-popup">
    <div class="attention-popup_inner">
      <p>Вам ужо споўнілася 18 гадоў?</p>
      <div class="attention-popup_actions">
        <button @click='openContent'>Так</button>
        <button>Не</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'attention-popup',
  data () {
    return {

    }
  },

  methods: {
    openContent: function (e) {
      e.preventDefault();
      this.$parent.attention = false;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/attention-popup.sass'
</style>
