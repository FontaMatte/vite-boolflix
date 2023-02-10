<script>

import { store } from '../store';

export default {

  name: 'AppHeader',
  data() {
    return {
      store
    };
  }
}
</script>

<template>
  <header class="bg-dark">

    <div class="container">
      <div class="row align-items-center justify-content-between p-3">
        <div class="title col-6">
          <a href="#" class="text-decoration-none">
            <h1 role="button" @click="$emit('mainPage')" class="text-danger d-inline">
              BOOLFLIX
            </h1>
          </a>
        </div>
        <div class="col-5 m-3">
          <div class="input-group">

            <input type="text" class="form-control" 
              placeholder="Inserisci il film che stai cercando"
              v-model="store.inputValue">

            <button @click="$emit('search')" class="input-group-text">
              CERCA
            </button>

          </div>
        </div>
      </div>
    </div>

  </header>
</template>

<style lang="scss" scoped>
  header {
    height: 100px;
    position: sticky;
    top: 0;
    left: 0;
    z-index: 5;
  }
  @import "../styles/partials/appHeader.scss";
</style>