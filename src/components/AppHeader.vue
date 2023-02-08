<script>

import { store } from '../store';

export default {

  name: 'AppHeader',
  data() {
    return {
      store
    };
  },
  components: {

  }
}
</script>

<template>
  <header>
      <div class="row">
        <div class="col-6 m-3">
          <div class="input-group mb-3">
            <input type="text" class="form-control" placeholder="Inserisci il film che stai cercando">
            <span class="input-group-text">CERCA</span>
          </div>
        </div>
      </div>
  </header>
</template>

<style lang="scss" scoped>
@import "../styles/partials/appHeader.scss";
</style>