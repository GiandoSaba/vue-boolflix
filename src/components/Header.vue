<template>
  <header>
    <div class="container-fluid">
      <div class="row my-2">
        <input
          v-model="searched"
          type="text"
          class="col-6 mx-4"
          @keyup.enter="$emit('takeSearch', searched)"
        >
        <button
          type="button"
          class="btn btn-success col-1"
          @click="$emit('takeSearch', searched)"
        >
          Search
        </button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      searched: '',
    };
  },
};
</script>

<style scoped lang="scss"></style>
