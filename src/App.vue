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
      apiKey:'aa915bc853b15971921a86116718a880'
    };
  },
  components: {
    AppHeader,
    AppMain,
    AppFooter
  },
  created() {

    this.getMainPage();    

  },
  methods: {
    // FUNZIONE PER TORNARE ALLA PAGINA PRINCIPALE
    getMainPage() {
      axios
          .get('https://api.themoviedb.org/3/movie/popular?api_key=aa915bc853b15971921a86116718a880&language=it-IT&page=1')
          .then((response) => {

            this.store.moviesList = response.data.results;
            this.store.tvSeriesList = '';

          });
    },

    getSearch() {

      this.makeSearch('movie');
      this.makeSearch('tv');
      
    },
    makeSearch(endpoint) {
      let url = 'https://api.themoviedb.org/3/search/';

      if ( this.store.inputValue != '') {
        axios
          .get(url + endpoint, {
            params: {
              api_key: this.apiKey,
              query: this.store.inputValue
            }
          })
          .then((response) => {

            if (endpoint == 'movie') {
             
              this.store.moviesList = response.data.results;
              console.log('movies',response.data.results);
              this.store.inputValue = '';
            }
            else {
              
              this.store.tvSeriesList = response.data.results;
              console.log('serie tv',response.data.results);
              this.store.inputValue = '';
            }
          });
      }
    }
  }
}
</script>

<template>

  <AppHeader @search="getSearch" @mainPage="getMainPage"/>

  <AppMain/>
  
  <AppFooter/>

</template>

<style lang="scss">
@import "./styles/global.scss";
</style>
