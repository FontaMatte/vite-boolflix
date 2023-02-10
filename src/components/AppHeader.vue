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
          <h1 role="button" @click="$emit('mainPage')" class="text-danger d-inline">
            BOOLFLIX
          </h1>
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
@import "../styles/partials/appHeader.scss";
</style>