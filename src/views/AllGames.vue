<template>
  <div id="app">
    <p>
      This is a list of all games in the planets.nu list. Used for testing table fields that lack variety in the home page (eg Created By and Password)
    </p>
    <GameTable options=""/>
  </div>
</template>

<script>
import axios from 'axios';
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