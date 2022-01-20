<template>
  <main>
    <div class="container-fluid">
      <div
        v-if="cards.films.length > 0"
        class="row gap-3 justify-content-center my-3 text-center mt-3"
      >
        <div class="col-12">
          <h1>Film</h1>
        </div>
        <Card
          v-for="(film,index) in cards.films"
          :key="index"
          :list="film"
        />
      </div>
      <div
        v-else
        class="row justify-content-center text-center"
      >
        <div class="col-12">
          <h1>
            Nessun film trovato
          </h1>
        </div>
      </div>
      <div
        v-if="cards.series.length > 0"
        class="row gap-3 justify-content-center my-3 text-center mt-3"
      >
        <div class="col-12">
          <h1>Serie TV</h1>
        </div>
        <Card
          v-for="(serie,index) in cards.series"
          :key="index"
          :list="serie"
        />
      </div>
      <div
        v-else
        class="row justify-content-center text-center"
      >
        <div class="col-12">
          <h1>
            Nessuna serie tv trovata
          </h1>
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
