<script>

export default {

  name: 'AppCard',
  props: {
    movieCard: Object
  },
  data() {
    return {
      
    }
  },
  computed: {

      rating() {
        return Math.ceil(this.movieCard.vote_average / 2);
      },
      ratingStars() {
        ratingStars = ''
        for (let i = 0; i < this.rating; i++) {
          ratingStars = `<i class="fa-solid fa-star"></i>`;
        }
      }
  }
  
}
</script>

<template>
<div>
  <div class="poster">
    <img class="img-fluid" :src="`https://image.tmdb.org/t/p/w300${movieCard.backdrop_path}`" 
      alt="Missing Image">
  </div>
  <ol>
    <li>{{ movieCard.title }}</li>

    <li>{{ movieCard.original_title }}</li>

    <li v-if="movieCard.original_language == 'it'">
      <img src="../assets/img/it.png" :alt="movieCard.original_language">
    </li>
    <li v-else-if="movieCard.original_language == 'en'">
      <img src="../assets/img/en.png" :alt="movieCard.original_language">
    </li>
    <li v-else-if="movieCard.original_language == 'es'">
      <img src="../assets/img/es.png" :alt="movieCard.original_language">
    </li>
    <li v-else-if="movieCard.original_language == 'fr'">
      <img src="../assets/img/fr.png" :alt="movieCard.original_language">
    </li>
    <li v-else>
      <img src="../assets/img/Unknown.png" :alt="movieCard.original_language">
    </li>

    <li>
      <span v-for="star in rating">
        <i class="fa-solid fa-star text-warning"></i>
      </span>
      <span v-for="star in 5 - rating">
        <i class="fa-solid fa-star text-secondary"></i>
      </span>
    </li>
    
  </ol>
</div>
</template>

<style lang="scss" scoped>

li {

  img {
    width: 30px;
  }
}

</style>