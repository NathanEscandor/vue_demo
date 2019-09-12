<template>
  <div id="app">
    {{games}}
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
      .then(res => (this.games = res))
      .catch(err => console.log(err));    
  }
}
</script>

<style>
</style>