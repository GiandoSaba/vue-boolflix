<template>
  <header>
    <div class="container-fluid p-0">
      <nav class="navbar navbar-dark bg-dark">
        <div class="container-fluid">
          <img
            src="../assets/logo.png"
            alt="logo"
          >
          <div class="d-flex">
            <input
              v-model="searched"
              class="form-control me-2 "
              type="search"
              placeholder="Cerca un film"
              aria-label="Search"
              @keyup.enter="$emit('takeSearch', searched)"
            >
            <button
              class="btn btn-outline-success"
              type="submit"
              @click="$emit('takeSearch', searched)"
            >
              <i class="fas fa-search" />
            </button>
          </div>
        </div>
      </nav>
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
