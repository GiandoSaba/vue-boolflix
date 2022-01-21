<template>
  <div
    id="app"
    class="bg-dark bg-gradient"
  >
    <Header @takeSearch="search($event)" />
    <Main
      v-if="loaded"
      :cards="searched"
      :popular="popularMovies"
    />
    <div
      v-else
      class="container-fluid homepage"
    >
      <div class="d-flex h-100">
        <h1 class="text-danger m-auto text-center fs-2">
          Benvenuto in <span class="d-block fs-1">Boolflix</span>
        </h1>
      </div>
    </div>
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
      query: 'https://api.themoviedb.org/3/',
      api_key: '89eb092bce881ee73ddbbdbb875f67e8',
      language: 'it',
      searchText: null,
      loaded: false,
      searched: {
        films: null,
        series: null,
      },
      popularMovies: {
        films: [],
        series: [],
      },
    };
  },
  watch: {
    searchText() {
      this.getFilms();
      this.getSeries();
    },
  },
  mounted() {
    this.getPopularFilms();
    this.getPopularSeries();
    setTimeout(() => {
      this.loaded = true;
    }, 1000);
  },
  methods: {
    search(text) {
      if (text !== '') {
        this.searchText = text;
      }
    },
    getFilms() {
      const endPoint = 'search/movie';
      const params = {
        api_key: this.api_key,
        language: this.language,
        query: this.searchText,
      };
      axios
        .get(`${this.query}${endPoint}`, { params })
        .then((result) => {
          if (result.data.results !== []) {
            this.searched.films = result.data.results;
          }
        })
        .catch((error) => {
          console.log(error);
        });
    },
    getSeries() {
      const endPoint = 'search/tv';
      const params = {
        api_key: this.api_key,
        language: this.language,
        query: this.searchText,
      };
      axios
        .get(`${this.query}${endPoint}`, { params })
        .then((result) => {
          if (result.data.results !== []) {
            this.searched.series = result.data.results;
          }
        })
        .catch((error) => {
          console.log(error);
        });
    },
    getPopularFilms() {
      const endPoint = 'trending/movie/week';
      const params = {
        api_key: this.api_key,
        language: this.language,
      };
      axios
        .get(`${this.query}${endPoint}`, { params })
        .then((result) => {
          this.popularMovies.films = result.data.results;
        })
        .catch((error) => {
          console.log(error);
        });
    },
    getPopularSeries() {
      const endPoint = 'trending/tv/week';
      const params = {
        api_key: this.api_key,
        language: this.language,
      };
      axios
        .get(`${this.query}${endPoint}`, { params })
        .then((result) => {
          this.popularMovies.series = result.data.results;
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
  .homepage {
    height: 80vh;
  }
}
</style>
