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
           
        <div class="d-flex align-items-center flex-wrap" >

          <AppCard v-for="movie in store.moviesList" :movieCard="movie"/>
          <AppCard v-for="serie in store.tvSeriesList" :movieCard="serie"/>

        </div>
    </div>
   
  </main>
</template>

<style lang="scss" scoped>
@import "../styles/partials/appMain.scss";
</style>