<template>
  <main class="py-1">
    <div
      v-if="cards.films || cards.series"
      class="container-fluid text-white"
    >
      <Cards
        v-show="cards.films"
        :list="cards.films"
        :title="'Film'"
      />
      <Cards
        v-show="cards.series"
        :list="cards.series"
        :title="'Serie TV'"
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
      />
      <Cards
        v-show="popular.series"
        :list="popular.series"
        :title="'Serie TV Popolari'"
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
  },
};
</script>

<style scoped lang="scss">

</style>
