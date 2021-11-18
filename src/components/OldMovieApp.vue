<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide on how to use this app,<br />
      check out the instructions tab.
    </p>
    <MyTable :headers="headers" :info="data" />
    <h2>
      </h2>
  </div>
</template>

<script>
import MyTable from "./Table.vue";

export default {
  name: "HelloWorld",
  components: {
    MyTable,
  },
  props: {
    msg: String,
    data: Object,
    headers: Array,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h2 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
