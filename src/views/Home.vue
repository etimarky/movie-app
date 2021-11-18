<template>
  <div class="home">
    <v-col class="text-right">
      <v-btn class="pink white--text">
        <v-icon text left small>mdi-email</v-icon>
        <span>contact me</span>
      </v-btn>
    </v-col>
    <movie-app />
  </div>
</template>

<script>
import MovieApp from "../components/MovieApp";

export default {
  name: "Home",

  components: {
    MovieApp,
  },
};
</script>
