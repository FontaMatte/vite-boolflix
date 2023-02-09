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
      defaultQuery: '&query="ritorno"',
    };
  },
  components: {
    AppHeader,
    AppMain,
    AppFooter
  },
  created() {

    // INVIO RICHIESTA MOVIES
    axios
      .get('https://api.themoviedb.org/3/search/movie'+ this.apiKey + this.defaultQuery)
      .then((response) => {
        console.log(response.data.results);
        this.store.moviesList = response.data.results
      });

    // INVIO RICHIESTA TV SERIES
    axios
      .get('https://api.themoviedb.org/3/search/tv'+ this.apiKey + this.defaultQuery)
      .then((response) => {
        // console.log(response.data.results);
        this.store.tvSeriesList = response.data.results
      });
  },
  methods: {

    // FUNZIONE PER OTTENERE MOVIES FILTRATI
    getMoviesList() {

      if ( this.store.inputValue != '') {
      axios
      .get('https://api.themoviedb.org/3/search/movie'+ this.apiKey + `&query="${this.store.inputValue}"`)
      .then((response) => {
        console.log(response.data.results);
        this.store.moviesList = response.data.results
      });
      }

      this.store.inputValue = '';

    },
    getTvSeriesList() {

      if ( this.store.inputValue != '') {
      axios
      .get('https://api.themoviedb.org/3/search/tv'+ this.apiKey + `&query="${this.store.inputValue}"`)
      .then((response) => {
        console.log(response.data.results);
        this.store.tvSeriesList = response.data.results
      });
      }

      this.store.inputValue = '';

      },

  }
}
</script>

<template>

  <AppHeader @search="getMoviesList(),getTvSeriesList()"/>

  <AppMain/>
  
  <AppFooter/>

</template>

<style lang="scss">
@import "./styles/global.scss";
</style>
