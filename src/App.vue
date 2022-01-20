<template>
  <div id="app">
    <Header @takeSearch="search($event)" />
    <Main
      :cards="cards"
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
      query: 'https://api.themoviedb.org/3/search/',
      api_key: '89eb092bce881ee73ddbbdbb875f67e8',
      language: 'it_IT',
      searchText: null,
      cards: {
        films: [],
        series: [],
      },
    };
  },
  methods: {
    search(text) {
      if (text !== '') {
        this.searchText = text;
        this.getFilms();
        this.getSeries();
      }
    },
    getFilms() {
      const endPoint = 'movie';
      const params = {
        api_key: this.api_key,
        language: this.language,
        query: this.searchText,
      };
      axios
        .get(`${this.query}${endPoint}`, { params })
        .then((result) => {
          console.log(result);
          this.cards.films = result.data.results;
        })
        .catch((error) => {
          console.log(error);
        });
    },
    getSeries() {
      const endPoint = 'tv';
      const params = {
        api_key: this.api_key,
        language: this.language,
        query: this.searchText,
      };
      axios
        .get(`${this.query}${endPoint}`, { params })
        .then((result) => {
          console.log(result);
          this.cards.series = result.data.results;
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
