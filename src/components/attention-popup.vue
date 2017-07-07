<template>
  <transition name="fade">
    <div class="attention-popup_overlay" v-if='attention'>
      <div class="attention-popup">
        <transition name="fade">
          <div v-if='!restriction' class="attention-popup_inner" key="question">
            <p>Вам ужо споўнілася <br> 18 гадоў?</p>
            <div class="attention-popup_actions">
              <button @click='openContent'>Так</button>
              <button @click='showRestriction'>Не</button>
            </div>
          </div>
          <div v-else class="attention-popup_inner restriction" key="answer">
            <p>На жаль, Вы не можаце зайсці на сайт.</p>
            <span>Вяртайцеся, калі Вам споўніцца 18.</span>
          </div>
        </transition>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'attention-popup',
  data () {
    return {
      attention: true,
      restriction: false
    }
  },

  methods: {
    openContent: function (e) {
      e.preventDefault();
      this.attention = false;
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
