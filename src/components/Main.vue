<template>
  <main>
    <div class="container-fluid">
      <div class="row mx-2">
        <ul
          v-for="(film,index) in films"
          :key="index"
          class="list-group col-3 my-3"
        >
          <li class="list-group-item">
            <h1 class="fs-5">
              Titolo
            </h1>
            <p>{{ film.title }}</p>
          </li>
          <li class="list-group-item">
            <h1 class="fs-5">
              Titolo Originale
            </h1>
            <p>{{ film.original_title }}</p>
          </li>
          <li class="list-group-item">
            <h1 class="fs-5">
              Lingua
            </h1>
            <p>{{ film.original_language }}</p>
          </li>
          <li class="list-group-item">
            <h1 class="fs-5">
              Voto
            </h1>
            <p>{{ film.vote_average }}</p>
          </li>
        </ul>
      </div>
    </div>
  </main>
</template>

<script>

export default {
  name: 'Main',
  props: ['films'],
  data() {
    return {
      filmsArray: this.films,
    };
  },
};
</script>

<style scoped lang="scss"></style>
