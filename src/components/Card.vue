<template>
  <ul
    class="list-group col-2 border"
  >
    <li
      v-show="list.poster_path"
      class="list-group-item border-0"
    >
      <img
        class="img-fluid"
        :src="`https://image.tmdb.org/t/p/w342${list.poster_path}`"
        :alt="list.title"
      >
    </li>
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
      <p>{{ list.vote_average }}</p>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'Card',
  // eslint-disable-next-line vue/require-prop-types
  props: ['list'],
  methods: {
    getFlag(lang) {
      if (lang === 'en') {
        return 'us';
      }
      return lang;
    },
  },
};
</script>

<style scoped lang="scss">
@import '~mdb-ui-kit/css/mdb.min.css';

</style>
