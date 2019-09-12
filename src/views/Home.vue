<template>
  <div id="app">
    <table>
      <tr>
        <th>Name</th>
        <th>Short Description</th>
        <th>Date Created</th>
        <th>Created By</th>
        <th>Host Days</th>
        <th>Password</th>
      </tr>
        <tr v-for="game in games" :key="game.id">
          <td>{{ game.name }} k</td>
          <td>{{ game.shortdescription }}</td>
          <td>{{ formatDate(game.datecreated) }} </td>
          <td>{{ game.createdby }}</td>
          <td>{{ game.hostdays }}</td>
          <td>{{ game.haspassword }}</td>
        </tr>

    </table>
  </div>
</template>

<script>
import axios from 'axios';
const dateFormat = require('dateformat');

export default {
  name: 'Home',
  components: {
  },
  methods: {
    formatDate(date) {
      return dateFormat(date, "mmmm:dd:yyyy");
    }
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
table {
  border-collapse: collapse;
  text-align: left;
}
td {
  border: 1px solid #dddddd;
  padding: 8px;
}
th {
  border: 1px solid #dddddd;
  padding: 8px;
  font-weight: bold[]
}
tr:nth-child(even) {
  background-color: #f2f2f2
}
</style>