<template>
  <div
    class="card col-2 p-0"
    @mouseover="active = true"
    @mouseleave="active = false"
  >
    <div
      v-if="!active"
      class="card-body"
    >
      <img
        v-if="list.poster_path"
        :src="`https://image.tmdb.org/t/p/original${list.poster_path}`"
        class="card-img-top"
        :alt="list.title"
      >
      <img
        v-else
        src="../assets/stock_image.png"
        class="card-img-top"
        :alt="list.title"
      >
    </div>
    <div
      v-else
      class="card-body card-description"
    >
      <ul class="list-group list-group-flush">
        <li class="list-group-item border-0">
          <h1 class="fs-5">
            Titolo
          </h1>
          <p>{{ (list.title) ? list.title : list.name }}</p>
        </li>
        <li
          v-show="list.title !== list.original_title || list.name !== list.original_name"
          class="list-group-item border-0"
        >
          <h1 class="fs-5">
            Titolo Originale
          </h1>
          <p>{{ (list.original_title) ? list.original_title : list.original_name }}</p>
        </li>
        <li
          v-show="list.overview"
          class="list-group-item border-0"
        >
          <h1 class="fs-5">
            Trama
          </h1>
          <p>{{ list.overview }}</p>
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
  data() {
    return {
      active: false,
    };
  },
  methods: {
    getFlag(lang) {
      switch (lang) {
        case 'en':
          return 'us';
        case 'ko':
          return 'kr';
        case 'ja':
          return 'jp';
        case 'ur':
          return 'pk';
        case 'zh':
          return 'cn';
        default:
          return lang;
      }
    },
    roundNumber(num) {
      return Math.round(num / 2);
    },
  },
};
</script>

<style scoped lang="scss">
@import '~mdb-ui-kit/css/mdb.min.css';
.card {
  cursor: pointer;
  .card-description {
    height: 440px;
    overflow: auto;
  }
}
</style>
