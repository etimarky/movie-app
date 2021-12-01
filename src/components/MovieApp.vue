<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/movie-logo.png')"
          class="my-3"
          contain
          height="100"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Movie Searching App
        </h1>

        <p class="subheading font-weight-regular">
          For more information on this page, please go to the instructions tab.
        </p>
      </v-col>
   
    
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'MovieApp',

    data: () => ({
     
    }),
  }
</script>
