<template>
  <div style="height: 500px; overflow: auto">
    <table>
      <tbody>
        <div v-for="i in info" v-bind:key="i.id">
          <tr>
          <th scope="col" v-for="h in headers" v-bind:key="h.id">{{ h }}</th>
        </tr>
          <tr v-for="j in i" v-bind:key="j.id">
            <td>{{ j.title }}</td>
            <td>{{ j.imdbID }}</td>
            <td>{{ j.tmdbID }}</td>
            <td>{{ j.imdbRating }}</td>
            <td>{{ j.genres }}</td>
            <td>{{ j.countries }}</td>
            <td>{{ j.year }}</td>
            <td>{{ j.runtime }}</td>
            <td>{{ j.age }}</td>
            <td>{{ j.streamingInfo }}</td>
            <td>{{ j.originalLanguage }}</td>
          </tr>
        </div>
      </tbody>
    </table>
  </div>
</template>


<script>
export default {
  name: "MyTable",
  props: {
    info: Object,
    headers: Array,
  },
  mounted() {},
};
</script>

<style scoped>
table {
  border-collapse: collapse;
  border-spacing: 0;
  width: 100%;
  border: 1px solid black;
  overflow-y: scroll;
}

th,
td {
  text-align: left;
  padding: 16px;
  border: 1px solid black;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}
</style>

