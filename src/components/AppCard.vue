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
  }
  
}
</script>

<template>
<section class="p-4">
    <div class="position-relative card-container">

      <img class="poster" :src="`https://image.tmdb.org/t/p/w342${movieCard.poster_path}`" :alt="movieCard.title">

      <div class="position-absolute top-0 start-0 bottom-0 end-0 py-4 px-3 on-hover">
        <h4 v-if="movieCard.title">Title: {{ movieCard.title }}</h4>
        <h4 v-if="movieCard.name">Title: {{ movieCard.name }}</h4>

        <h5 v-if="movieCard.original_title">Original Title: {{ movieCard.original_title }}</h5>
        <h5 v-if="movieCard.original_name">Original Title: {{ movieCard.original_name }}</h5>

        <span v-if="movieCard.original_language == 'it'">
          <img src="../assets/img/it.png" :alt="movieCard.original_language">
        </span>
        <span v-else-if="movieCard.original_language == 'en'">
          <img src="../assets/img/en.png" :alt="movieCard.original_language">
        </span>
        <span v-else-if="movieCard.original_language == 'es'">
          <img src="../assets/img/es.png" :alt="movieCard.original_language">
        </span>
        <span v-else-if="movieCard.original_language == 'fr'">
          <img src="../assets/img/fr.png" :alt="movieCard.original_language">
        </span>
        <span v-else>
          <img src="../assets/img/Unknown.png" :alt="movieCard.original_language">
        </span>

        <div>
          <span>
            <i v-for="star in rating" class="fa-solid fa-star text-warning"></i>
          </span>
          <span>
            <i v-for="star in 5 - rating" class="fa-solid fa-star text-secondary"></i>
          </span>
        </div>
      </div>

    </div>
</section>
</template>

<style lang="scss" scoped>
section {
  width: calc(100% / 3);
  height: auto;

  .card-container {
        height: 450px;
        overflow: hidden;
        border: 1.5px solid white;
        border-radius: 5px;
  }
  .poster {
    height: 450px;
    width: 100%;
    object-fit: cover;
    object-position: top center;
  }
  .on-hover {
    display: none;

    background-color: rgba(0, 0, 0, 0.8);
    color: white;
    text-align: center;

    img {
      width: 30px;
    }

  }
  &:hover .on-hover {
    display: block;
  }
}

</style>