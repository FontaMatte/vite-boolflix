<script>

export default {

  name: 'AppCard',
  props: {
    movieCard: Object
  }
}
</script>

<template>
<div>
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

    <li>{{ movieCard.vote_average }}</li>
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