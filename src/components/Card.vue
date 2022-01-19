<template>
  <ul class="list-group col-3 my-3">
    <li class="list-group-item">
      <h1 class="fs-5">
        Titolo
      </h1>
      <p>{{ filmObj.title }}</p>
    </li>
    <li class="list-group-item">
      <h1 class="fs-5">
        Titolo Originale
      </h1>
      <p>{{ filmObj.original_title }}</p>
    </li>
    <li class="list-group-item">
      <i :class="'flag flag-' + filmObj.original_language" />
    </li>
    <li class="list-group-item">
      <h1 class="fs-5">
        Voto
      </h1>
      <p>{{ filmObj.vote_average }}</p>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'Card',
  // eslint-disable-next-line vue/require-prop-types
  props: ['filmObj'],
};
</script>

<style scoped lang="scss">
@import '~mdb-ui-kit/css/mdb.min.css';

</style>
