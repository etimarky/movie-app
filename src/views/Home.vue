<template>
  <div class="home">
    <div class="wishlist">
      <v-simple-table>
        <template v-slot:default>
          <thead>
            <th>Wish List</th>
            <tr>
              <th class="text-left">Title</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in selectedMovies" :key="item.id">
              <td>{{ item.title }}</td>
            </tr>
          </tbody>
        </template>
      </v-simple-table>
    </div>

    <div class="main">
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
        <v-data-table
          :search="search"
          :headers="headers"
          :items="movies"
          item-key="imdbID"
          v-model="selectedRows"
          class="elevation-1"
        >
          <template v-slot:item="{ item }">
            <tr
              :class="selectedRows.indexOf(item.id) > -1 ? 'orange' : ''"
              @click="rowClicked(item)"
            >
              <td>{{ item.title }}</td>
              <td>{{ item.imdbID }}</td>
              <td>{{ item.tmdbID }}</td>
              <td>{{ item.imdbRating }}</td>
              <td>{{ item.genres }}</td>
              <td>{{ item.year }}</td>
              <td>{{ item.runtime }}</td>
              <td>{{ item.age }}</td>
              <td>{{ item.originalLanguage }}</td>
            </tr>
          </template>
        </v-data-table>
      </v-card>
    </div>
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
    selectedRows: [],
    selectedMovies: [],
    movies: [],
    headers: [],
    wishlistHeaders: [{ text: "title" }],
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
      // streamingInfo removed
      { text: "originalLanguage", value: "originalLanguage" },
    ];
    return (this.movies = res.data.message);
  },
  methods: {
    async rowClicked(row) {
      this.toggleSelection(row);

      try {
        await axios.post("http://localhost:8081/selected", {movie: row} );
      } catch (err) {
        console.log(err.message);
      }

    },
    toggleSelection(row) {
      let id = row.id;
      if (this.selectedRows.includes(id)) {
        this.selectedRows = this.selectedRows.filter(
          (selectedID) => selectedID !== id
        );
        this.selectedMovies = this.selectedMovies.filter(
          (selectedMovie) => selectedMovie !== row
        );
      } else {
        this.selectedRows.push(id);
        this.selectedMovies.push(row);
      }
    },
  },
};
</script>
<style scoped>
.wishlist {
  height: 100%; /* Full-height: remove this if you want "auto" height */
  width: 260px; /* Set the width of the sidebar */
  position: fixed; /* Fixed Sidebar (stay in place on scroll) */
  z-index: 1; /* Stay on top */
  top: 0; /* Stay at the top */
  right: 0;
  background-color: white; /* Black */
  overflow-x: hidden; /* Disable horizontal scroll */
  padding-top: 20px;
}

/* Style page content */
.main {
  margin-right: 260px; /* Same as the width of the sidebar */
  padding: 0px 10px;
}
</style>