<template>
  <div class="home">
    <div class="home_content">
      <div class="home_info">
        <div class="socials">
          <a href="#" class="fb" onclick="window.open('http://m.facebook.com/sharer.php?u=http://event.edenkit.com', 'sharer', 'toolbar=0,status=0,width=626,height=436,top=200,left=200');return false;">Facebook</a>
          <a href="#" class="vk" onclick="window.open('http://vk.com/share.php?url=http://event.edenkit.com', 'sharer', 'toolbar=0,status=0,width=626,height=436,top=200,left=200');return false;">Vkontakte</a>
          <a href="#" class="tweet" onclick="window.open('http://www.twitter.com/share?url=http://event.edenkit.com', 'sharer', 'toolbar=0,status=0,width=626,height=436,top=200,left=200');return false;">Twitter</a>
        </div>
        <a class="rules_mobile" href="rules.pdf" target="_blank">Спамуй поўныя правілы</a>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'home',
    data () {
      return {

      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='sass' scoped>
  @import '../assets/styles/home.sass'
</style>
