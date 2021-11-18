<template>
  <v-data-table
    dense
    :headers="headers"
    :items="info"
    item-key="name"
    class="elevation-1"
  ></v-data-table>
</template>


<script>

export default {
  name: "MyTable",
  props: {
    info: Object,
    headers: Array,
  }
};
</script>
