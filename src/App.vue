<script>
import axios from 'axios';
import { store } from './store.js';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';

export default {
  name: 'App',
  data() {
    return {
      store,
      apiKey:'?api_key=aa915bc853b15971921a86116718a880',
      defaultQuery: '&query="ritorno al"',
    };
  },
  components: {
    AppHeader,
    AppMain,
    AppFooter
  },
  created() {

    axios
      .get('https://api.themoviedb.org/3/search/movie'+ this.apiKey + this.defaultQuery)
      .then((response) => {
        console.log(response.data.results);
        this.store.moviesList = response.data.results
      });

    axios
      .get('https://api.themoviedb.org/3/search/tv'+ this.apiKey + this.defaultQuery)
      .then((response) => {
        console.log(response.data.results);
        this.store.tvSeriesList = response.data.results
      });
  },
  methods: {

  }
}
</script>

<template>

  <AppHeader/>

  <AppMain/>
  
  <AppFooter/>

</template>

<style lang="scss">
@import "./styles/global.scss";
</style>
