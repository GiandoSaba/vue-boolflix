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
        :alt="title"
      >
      <img
        v-else
        src="../assets/stock_image.png"
        class="card-img-top"
        :alt="title"
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
          <p>{{ title }}</p>
        </li>
        <li
          v-show="title !== originalTitle"
          class="list-group-item border-0"
        >
          <h1 class="fs-5">
            Titolo Originale
          </h1>
          <p>{{ originalTitle }}</p>
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
        <li
          v-show="list.cast"
          class="list-group-item border-0"
        >
          <h1 class="fs-5">
            Attori principali
          </h1>
          <p
            v-for="actor in list.cast"
            :key="filmid+actor"
          >
            {{ actor }}
          </p>
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
        <li class="list-group-item border-0">
          <h1 class="fs-5">
            <a
              :href="`https://www.themoviedb.org/${getUrl()}`"
              target="_blank"
            >Cerca su TMDB</a>
          </h1>
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
    type: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      active: false,
      title: (this.type === 'movie') ? this.list.title : this.list.name,
      originalTitle: (this.type === 'movie') ? this.list.original_title : this.list.original_name,
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
    getUrl() {
      return `${this.type}/${this.list.id}`;
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
