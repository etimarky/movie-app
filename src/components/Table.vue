<template>
    <v-data-table
      :headers="headers"
      :items="items"
      :items-per-page="5"
      class="elevation-1"
    ></v-data-table>
</template>


<script>
export default {
  name: 'MyTable',
  props: {
    headers: Array,
    items: Array
  }
}
</script>

