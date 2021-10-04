<template>
  <div class="home">
    <img alt="Movie Logo" src="../assets/movie-logo.png" height="200px" width="700px">
    <MovieApp msg="Welcome to the Movie Searching App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import MovieApp from '@/components/MovieApp.vue'

export default {
  name: 'Home',
  components: {
    MovieApp
  }
}
</script>
