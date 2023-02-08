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
    <li>{{ movieCard.original_language }}</li>
    <li>{{ movieCard.vote_average }}</li>
  </ol>
</div>
</template>

<style lang="scss" scoped>
</style>