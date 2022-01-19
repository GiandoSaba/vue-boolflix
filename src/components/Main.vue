<template>
  <main>
    <div class="container-fluid">
      <div class="row mx-2">
        <Card
          v-for="(film,index) in films"
          :key="index"
          :list="film"
        />
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
  // eslint-disable-next-line vue/require-prop-types
  props: ['films'],
};
</script>

<style scoped lang="scss"></style>
