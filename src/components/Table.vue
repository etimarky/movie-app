<template>
  <table>
    <tbody>
      <tr>
        <th scope = "col" v-for="h in headers" v-bind:key="h.id">{{ h }}</th>
      </tr>
      <div v-for="i in info" v-bind:key="i.id">
        <tr v-for="j in i" v-bind:key="j.id">
          <td>{{ j.title }}</td>
          <td>{{ j.firstAirYear }}</td>
          <td>{{ j.imdbID }}</td>
          <td>{{ j.tmdbID }}</td>
          <td>{{ j.imdbRating }}</td>
          <td>{{ j.countries }}</td>
          <td>{{ j.year }}</td>
        </tr>
      </div>
    </tbody>
  </table>
</template>


<script>
export default {
  name: "MyTable",
  props: {
    info: Object,
    headers: Array,
  },
};
</script>

<style scoped>
table {
  width: 100%;
}

th,
tr,
td {
  padding: 15px 0;
  text-align: center;
  border: 1px dotted gray;
}
</style>

