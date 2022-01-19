<template>
  <div id="app">
    <Header @takeSearch="getFilms($event)" />
    <Main
      :films="films"
      :series="series"
    />
  </div>
</template>

<script>
import axios from 'axios';

import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data() {
    return {
      queryFilms:
        'https://api.themoviedb.org/3/search/movie?api_key=89eb092bce881ee73ddbbdbb875f67e8&query=',
      films: null,
    };
  },
  methods: {
    getFilms(value) {
      axios
        .get(this.queryFilms + value)
        .then((result) => {
          this.films = result.data.results;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";
</style>
