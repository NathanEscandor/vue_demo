<template>
  <div>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <table align="center">
      <tr>
        <th>Name</th>
        <th>Short Description</th>
        <th>Date Created</th>
        <th>Created By</th>
        <th>Host Days</th>
        <th>Password</th>
      </tr>
      <tr v-for="game in games" :key="game.id" v-on:click="goToGame(game.id)" style="cursor: pointer;">
        <td>{{ game.name }}</td>
        <td>{{ game.shortdescription }}</td>
        <td>{{ formatDate(game.datecreated) }} </td>
        <td v-if="game.createdby !== 'none'">{{ game.createdby }}</td><td v-else></td>
        <td style="white-space: nowrap;">{{ game.hostdays }}</td>
        <td v-if="game.haspassword"><i class="fa fa-lock" style="font-size:36px"></i></td><td v-else></td>
      </tr>

    </table>
  </div>
</template>

<script>
import axios from 'axios';
const dateFormat = require('dateformat');
const ordinal = require('ordinal');

export default {
  name: 'GameTable',
  props: ['options'],
  methods: {
    formatDate(date) {
      const split_date = dateFormat(date, "mmmm dd yyyy").split(" ");
      const formatted_date = split_date[0] + " " + ordinal(parseInt(split_date[1])) + " " + split_date[2];
      return formatted_date;
    },
    goToGame(id) {
      window.location.href= 'https://planets.nu/#/sector/' + id;
    }
  },
  data() {
    return {
      games: null
    }
  },
  created() {
    axios.get('http://api.planets.nu/games/list?' + this.options)
      .then(res => (this.games = res.data))
      .catch(err => console.log(err));
  }
}
</script>

<style>
table {
  display: block;
  width: 60%;
  border-collapse: collapse;
  text-align: left;
  font-family:'Times New Roman', Times, serif
}
td {
  border: 2px solid black;
  padding: 8px;
}
th {
  border: 2px solid black;
  padding: 8px;
  font-weight: bold[]
}
tr:nth-child(even) {
  background-color: #f2f2f2
}
</style>