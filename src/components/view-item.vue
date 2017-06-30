<template>
  <div class="view_item" :class='className'>
    <h2 class="view_item_title">{{text}}</h2>
    <span class="voice">{{voice}}</span>
    <div class="item_overlay">
      <button class="more">Падрабязней</button>
      <button class="vote">Галасаваць</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'view-item',

    props: ['voice', 'text', 'className'],

    data () {
      return {

      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/view-item.sass'
</style>
