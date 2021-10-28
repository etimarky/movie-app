<template>
  <div class="home">
    <img
      alt="Movie Logo"
      src="../assets/movie-logo.png"
      height="200px"
      width="700px"
    />
    <MovieApp
      msg="Welcome to the Movie Searching App"
      :data="info"
      :headers="headers"
    />
  </div>
</template>

<script>
// @ is an alias to /src
import MovieApp from "@/components/MovieApp.vue";
import axios from "axios";

export default {
  name: "Home",
  data: function () {
    return {
      info: {},
      headers: Array,
    };
  },
  // props: {
  //   headers:
  // },
  components: {
    MovieApp,
  },
  async mounted() {
    let res = await axios.get("http://localhost:8080/");
    this.headers = [
      "title",
      "first year aired",
      "imdbID",
      "tmdbID",
      "imdbRating",
      "countries",
      "year",
    ];
    return (this.info = res.data);
  },
};
</script>
