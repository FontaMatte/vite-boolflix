<script>

import { store } from '../store';
import AppCard from './AppCard.vue';

export default {

  name: 'AppMain',
  data() {
    return {
      store
    };
  },
  components: {
    AppCard
  }
  
}
</script>

<template>
  <main class="bg-secondary">

    <div class="container pt-5">
        <!-- LISTA MOVIES -->
        <h1 v-if="store.moviesList" class="ms-4">FILM</h1>     
        <div class="d-flex align-items-center flex-wrap" >

          <AppCard v-for="movie in store.moviesList" :movieCard="movie"/>

        </div>
        <!-- LISTA TV SERIES -->
        <h1 v-if="store.tvSeriesList" class="ms-4">SERIE TV</h1>
        <div class="d-flex align-items-center flex-wrap" >

          <AppCard v-for="serie in store.tvSeriesList" :movieCard="serie"/>

        </div>
    </div>
   
  </main>
</template>

<style lang="scss" scoped>
@import "../styles/partials/appMain.scss";
</style>