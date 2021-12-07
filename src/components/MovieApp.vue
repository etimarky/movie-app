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
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "MovieApp",

  data: () => ({
  }),
 
};
</script>
