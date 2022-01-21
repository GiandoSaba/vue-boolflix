<template>
  <main class="py-1">
    <div
      v-if="cards.films || cards.series"
      class="container-fluid text-white"
    >
      <div
        v-show="cards.films"
        class="row gap-3 justify-content-center my-3 text-center p-3"
      >
        <div
          v-if="cards.films.length > 0"
          class="col-12"
        >
          <h1>Films</h1>
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
      >
        <div
          v-if="cards.series.length > 0"
          class="col-12"
        >
          <h1>Serie TV</h1>
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
      class="container-fluid text-white"
    >
      <div
        class="row justify-content-center my-3 text-center p-3"
      >
        <div
          class="col-12"
        >
          <h1>Benvenuto in BOOLFLIX</h1>
        </div>
      </div>
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
};
</script>

<style scoped lang="scss"></style>
