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
      defaultQuery: '&query="star"',
    };
  },
  components: {
    AppHeader,
    AppMain,
    AppFooter
  },
  created() {

    // INVIO RICHIESTA MOVIES
    this.getMoviesList();

    // INVIO RICHIESTA TV SERIES
    this.getTvSeriesList();
  },
  methods: {

    // FUNZIONE RICHIESTA API MOVIES
    getMoviesList() {
      axios
      .get('https://api.themoviedb.org/3/search/movie'+ this.apiKey + this.defaultQuery)
      .then((response) => {
        console.log('movies list', response.data.results);
        this.store.moviesList = response.data.results
      });
    },
    // FUNZIONE RICHIESTA API TV SERIES
    getTvSeriesList() {
    axios
      .get('https://api.themoviedb.org/3/search/tv'+ this.apiKey + this.defaultQuery)
      .then((response) => {
        // console.log(response.data.results);
        this.store.tvSeriesList = response.data.results
      })
    },

    // FUNZIONE PER OTTENERE MOVIES FILTRATI
    getMoviesListFiltered() {

      if ( this.store.inputValue != '') {
        axios
        .get('https://api.themoviedb.org/3/search/movie'+ this.apiKey + `&query="${this.store.inputValue}"`)
        .then((response) => {

          console.log('movies list filtrata',response.data.results);
          
          if (response.data.results != []) {
            this.store.moviesList = response.data.results; 
          }
          else {
            this.getMoviesList();
          }
        })   
      }

      this.store.inputValue = '';

    },
    // FUNZIONE PER OTTENERE TV SERIES FILTRATE
    getTvSeriesListFiltered() {

      if ( this.store.inputValue != '') {
      axios
      .get('https://api.themoviedb.org/3/search/tv'+ this.apiKey + `&query="${this.store.inputValue}"`)
      .then((response) => {
        // console.log(response.data.results);
        this.store.tvSeriesList = response.data.results
      })
      // .catch((error) => {

      //   this.getTvSeriesList();

      // })
      }

      this.store.inputValue = '';

    },

  }
}
</script>

<template>

  <AppHeader @search="getMoviesListFiltered(),getTvSeriesListFiltered()"/>

  <AppMain/>
  
  <AppFooter/>

</template>

<style lang="scss">
@import "./styles/global.scss";
</style>
