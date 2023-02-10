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
        <h1 class="ms-4">FILM</h1>
        <h4 v-if="store.moviesList == false" class="ms-4">Nessun Risultato in 'FILM'</h4>   
        <div class="d-flex align-items-center flex-wrap" >

            <AppCard v-for="movie in store.moviesList" :movieCard="movie"/>

        </div>

        <!-- LISTA TV SERIES -->
        <h1 class="ms-4">SERIE TV</h1>
        <h4 v-if="store.tvSeriesList == false" class="ms-4">Nessun Risultato in 'SERIE TV'</h4> 
        <div class="d-flex align-items-center flex-wrap" >

          <AppCard v-for="serie in store.tvSeriesList" :movieCard="serie"/>

        </div>
    </div>
   
  </main>
</template>

<style lang="scss" scoped>
  main {
      min-height: calc(100vh - 100px);
  }
  @import "../styles/partials/appMain.scss";
</style>