<template>
  <main class="py-1">
    <select
      id="genresSelect"
      v-model="selectedGenre"
      name="genres"
      class="mx-4"
    >
      <option value="">
        Filtra per genere
      </option>
      <option
        v-for="genre in genres.movie"
        :key="genre.id"
        :value="genre.name"
      >
        {{ genre.name }}
      </option>
    </select>
    <div
      v-if="cards.films || cards.series"
      class="container-fluid text-white"
    >
      <Cards
        v-show="cards.films"
        :list="cards.films"
        :title="'Film'"
        :type="'movie'"
        :genres="genres"
        :selected-genre="selectedGenre"
      />
      <Cards
        v-show="cards.series"
        :list="cards.series"
        :title="'Serie TV'"
        :type="'tv'"
        :genres="genres"
        :selected-genre="selectedGenre"
      />
    </div>
    <div
      v-else
      class="container-fluid text-white"
    >
      <Cards
        v-show="popular.films"
        :list="popular.films"
        :title="'Film Popolari'"
        :type="'movie'"
        :genres="genres"
        :selected-genre="selectedGenre"
      />
      <Cards
        v-show="popular.series"
        :list="popular.series"
        :title="'Serie TV Popolari'"
        :type="'tv'"
        :genres="genres"
        :selected-genre="selectedGenre"
      />
    </div>
  </main>
</template>

<script>
import Cards from './Cards.vue';

export default {
  name: 'Main',
  components: {
    Cards,
  },
  props: {
    cards: {
      type: Object,
      default() {
        return {};
      },
    },
    popular: {
      type: Object,
      default() {
        return {};
      },
    },
    genres: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  data() {
    return {
      selectedGenre: '',
      allGenres: this.getAllGenres(),
    };
  },
  methods: {
    getAllGenres() {
      const allGenres = [];
      this.genres.movie.forEach((element) => {
        if (!allGenres.includes(element.name)) {
          allGenres.push(element.name);
        }
      });
      this.genres.tv.forEach((element) => {
        if (!allGenres.includes(element.name)) {
          allGenres.push(element.name);
        }
      });
      return allGenres;
    },
  },
};
</script>

<style scoped lang="scss">

</style>
