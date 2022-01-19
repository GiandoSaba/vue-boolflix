<template>
  <ul
    class="list-group col-3 my-3"
  >
    <li class="list-group-item">
      <h1 class="fs-5">
        Titolo
      </h1>
      <p>{{ list.title }}</p>
    </li>
    <li class="list-group-item">
      <h1 class="fs-5">
        Titolo Originale
      </h1>
      <p>{{ list.original_title }}</p>
    </li>
    <li class="list-group-item">
      <h1 class="fs-5">
        Lingua
      </h1>
      <i :class="'flag flag-' + getFlag(list.original_language)" />
    </li>
    <li class="list-group-item">
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
