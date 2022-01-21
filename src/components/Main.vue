<template>
  <main class="py-1">
    <div
      v-if="cards.films || cards.series"
      class="container-fluid text-white"
    >
      <div
        v-show="cards.films"
        class="row gap-3 justify-content-center my-3 text-center p-3"
        :class="(!activeFilms) ? 'show_off' : ''"
      >
        <div
          v-if="cards.films.length > 0"
          class="col-12"
        >
          <div class="container-fluid d-flex justify-content-between align-items-end my_nav_menu">
            <h1>Film</h1>
            <h5
              v-show="!activeFilms"
              @click="activeFilms = !activeFilms"
            >
              Sfoglia tutti
            </h5>
            <h5
              v-show="activeFilms"
              @click="activeFilms = !activeFilms"
            >
              Nascondi
            </h5>
          </div>
        </div>
        <div
          v-else
          class="col-12"
        >
          <h2>
            Nessun film trovato
          </h2>
        </div>
        <Card
          v-for="(film) in cards.films"
          :key="film.id"
          :list="film"
        />
      </div>
      <div
        v-show="cards.series"
        class="row gap-3 justify-content-center my-3 text-center p-3"
        :class="(!activeSeries) ? 'show_off' : ''"
      >
        <div
          v-if="cards.series.length > 0"
          class="col-12"
        >
          <div class="container-fluid d-flex justify-content-between align-items-end my_nav_menu">
            <h1>Serie Tv</h1>
            <h5
              v-show="!activeSeries"
              @click="activeSeries = !activeSeries"
            >
              Sfoglia tutti
            </h5>
            <h5
              v-show="activeSeries"
              @click="activeSeries = !activeSeries"
            >
              Nascondi
            </h5>
          </div>
        </div>
        <div
          v-else
          class="col-12"
        >
          <h2>
            Nessuna serie tv trovata
          </h2>
        </div>
        <Card
          v-for="(serie) in cards.series"
          :key="serie.id"
          :list="serie"
        />
      </div>
    </div>
    <div
      v-else
      class="container-fluid text-white home_page d-flex"
    >
      <h1 class="m-auto text-danger text-center">
        Benvenuto in <span class="d-block fs-1 fw-bold">BOOLFLIX</span>
      </h1>
    </div>
  </main>
</template>

<script>
import Card from './Card.vue';

export default {
  name: 'Main',
  components: {
    Card,
  },
  props: {
    cards: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  data() {
    return {
      activeFilms: false,
      activeSeries: false,
    };
  },
};
</script>

<style scoped lang="scss">
.show_off {
  height: 540px;
  overflow: hidden;
}

.my_nav_menu {
  h5:hover {
    cursor: pointer;
    text-decoration: underline;
  }
}

.home_page {
  height: 500px;
}

</style>
