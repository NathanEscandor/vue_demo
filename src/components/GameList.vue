<template>
  <div>
    {{ games }}
  </div>
</template>

<script>
import Game from './Game.vue';
import axios from 'axios';

export default {
  name: "GameList",
  components: {
    Game
  },
  props: ["games"],
  data() {
    return {
      games: null
    }
  },
  mounted() {
    axios.get('http://api.planets.nu/games/list?status=1')
      .then(res => (this.games = res))
      .catch(err => console.log(err));    
  }
}
</script>

<style scoped>

</style>

