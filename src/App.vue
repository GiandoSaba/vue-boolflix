<template>
  <div
    id="app"
    class="bg-dark bg-gradient"
  >
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
        films: null,
        series: null,
      },
    };
  },
  watch: {
    searchText() {
      this.getFilms();
      this.getSeries();
    },
  },
  methods: {
    search(text) {
      if (text !== '') {
        this.searchText = text;
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
          if (result.data.results !== []) {
            this.cards.films = result.data.results;
          }
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
          if (result.data.results !== []) {
            this.cards.series = result.data.results;
          }
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
#app {
  width: 100%;
  height: 100vh;
  overflow: auto;
}
</style>
