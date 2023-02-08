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
      store
    };
  },
  components: {
    AppHeader,
    AppMain,
    AppFooter
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
