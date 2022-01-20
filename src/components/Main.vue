<template>
  <main>
    <div class="container-fluid">
      <div class="row gap-3 justify-content-center my-3 text-center">
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
