<template>
  <div class="home">
    <v-col class="text-right">
      <v-btn class="pink white--text">
        <v-icon text left small>mdi-email</v-icon>
        <span>contact me</span>
      </v-btn>
    </v-col>
    <movie-app />
    <v-card>
      <v-card-title>
        <v-text-field
          v-model="search"
          append-icon="mdi-magnify"
          label="Search"
          single-line
          hide-details
        ></v-text-field>
      </v-card-title>
      </v-card>
      <v-data-table
        v-model="selected"
        :headers="headers"
        :items="movies"
        :single-select="singleSelect"
        :search="search"
        item-key="name"
        show-select
        class="elevation-1"
      >
        <template v-slot:top>
          <v-switch
            v-model="singleSelect"
            label="Single select"
            class="pa-3"
          ></v-switch>
        </template>
      </v-data-table>
  </div>
</template>

<script>
import MovieApp from "../components/MovieApp";
import axios from "axios";

export default {
  name: "Home",

  components: {
    MovieApp,
  },
  data: () => ({
    search: "",
    singleSelect: false,
    selected: [],
    movies: [],
    headers: [],
  }),
  async mounted() {
    let res = await axios.get("http://localhost:8081/movies");
    this.headers = [
      { text: "title", value: "title", align: "start", sortable: false },
      { text: "imdbID", value: "imdbID" },
      { text: "tmdbID", value: "tmdbID" },
      { text: "imdbRating", value: "imdbRating" },
      { text: "genres", value: "genres" },
      // countries removed
      { text: "year", value: "year" },
      { text: "runtime", value: "runtime" },
      { text: "age", value: "age" },
      // {text: "streamingInfo", value: "streamingInfo"},
      { text: "originalLanguage", value: "originalLanguage" },
    ];
    return (this.movies = res.data.message);
  },
};
</script>
