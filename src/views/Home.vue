<template>
  <div id="app">
    <div v-for="game in games" :key="game.id">
      {{game.name}}
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'Home',
  components: {
  },
  data() {
    return {
      games: null
    }
  },
  mounted() {
    axios.get('http://api.planets.nu/games/list?status=1')
      .then(res => (this.games = res.data))
      .catch(err => console.log(err));    
  }
}
</script>

<style>
</style>