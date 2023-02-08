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
  <main>

    <div class="container">
      <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4">
        
        <!-- CICLO L'ARRAY DEI RISULATI CHE MI VENGONO RESTITUITI -->
        <div class="col border" v-for="movie in store.moviesList">

          <AppCard :movieCard="movie"/>

        </div>
      </div>
    </div>
   
  </main>
</template>

<style lang="scss" scoped>
@import "../styles/partials/appMain.scss";
</style>