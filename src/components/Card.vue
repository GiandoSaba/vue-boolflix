<template>
  <div class="card col-2 p-0">
    <img
      :src="`https://image.tmdb.org/t/p/original${list.poster_path}`"
      class="card-img-top"
      :alt="list.title"
    >
    <div class="card-body">
      <ul class="list-group list-group-flush">
        <li class="list-group-item border-0">
          <h1 class="fs-5">
            Titolo
          </h1>
          <p>{{ (list.title) ? list.title : list.name }}</p>
        </li>
        <li
          class="list-group-item border-0"
        >
          <h1 class="fs-5">
            Titolo Originale
          </h1>
          <p>{{ (list.original_title) ? list.original_title : list.original_name }}</p>
        </li>
        <li class="list-group-item border-0">
          <h1 class="fs-5">
            Lingua
          </h1>
          <i :class="'flag flag-' + getFlag(list.original_language)" />
        </li>
        <li class="list-group-item border-0">
          <h1 class="fs-5">
            Voto
          </h1>
          <i
            v-for="n in 5"
            :key="n"
            :class="(n <= roundNumber(list.vote_average)) ? 'fas fa-star' : 'far fa-star'"
          />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    list: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  methods: {
    getFlag(lang) {
      if (lang === 'en') {
        return 'us';
      }
      return lang;
    },
    roundNumber(num) {
      const number = parseFloat(num);
      return Math.round(number / 2);
    },
  },
};
</script>

<style scoped lang="scss">
@import '~mdb-ui-kit/css/mdb.min.css';
</style>
