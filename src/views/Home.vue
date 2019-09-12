<template>
  <div id="app">
    <GameTable options="status=1"/>
  </div>
</template>

<script>
import GameTable from '../components/GameTable';

export default {
  name: 'Home',
  components: {
    GameTable
  }
}
</script>

<style>
</style>