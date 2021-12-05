<template>
  <v-container>
    <v-row>
      <v-col cols="auto">
        <h1 class="text-center">Movie Searching App</h1>
        <v-img
          :src="require('../assets/movie-logo.png')"
          class="my-3"
          contain
          height="100"
        />
      </v-col>
      <v-col>
        <v-card>This is my table </v-card>
      </v-col>
      <!-- <v-col width="100px">
          <v-subheader>Wish List</v-subheader>
          <v-data-table
            :headers="headers"
            :items="selectedRows"
            class="elevation-1"
          ></v-data-table> -->
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "MovieApp",

  data: () => ({
    headers: [],
    selectedRows: [],
  }),
  mounted() {
    this.headers = [
      { text: "title", value: "title", align: "start", sortable: false },
    ];
    return (this.headers = this.headers);
  },
};
</script>
