<template>
  <div class="home">
   
    <movie-app selectedRows="selectedRows"/>
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
      // streamingInfo removed
      { text: "originalLanguage", value: "originalLanguage" },
    ];
    return (this.movies = res.data.message);
  },
  methods: {
    rowClicked(row) {
      this.toggleSelection(row.id);
      console.log(row);
      // await axios.post("http://localhost:8081/selected", row)
    },
    toggleSelection(keyID) {
      if (this.selectedRows.includes(keyID)) {
        this.selectedRows = this.selectedRows.filter(
          (selectedKeyID) => selectedKeyID !== keyID
        );
      } else {
        this.selectedRows.push(keyID);
      }
    },
  },
};
</script>
