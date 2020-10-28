<template>
  <div id="app">
    <table class="table">
      <thead>
        <tr>
          <th>SepalLength</th>
          <th>SepalWidth</th>
          <th>PetalLength</th>
          <th>PetalWidth</th>
          <th>Species</th>
        </tr>
      </thead>
      <tbody>
        <tr :key="flower.species" v-for="flower in irisSet">
          <td>{{ flower.sepalLength }}</td>
          <td>{{ flower.sepalWidth }}</td>
          <td>{{ flower.petalLength }}</td>
          <td>{{ flower.petalWidth }}</td>
          <td>{{ flower.species }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "RenderTest",
  data() {
    return {
      dataSet: {},
    };
  },
  computed: {
    irisSet() {
      return this.dataSet;
    },
  },
  created() {
    fetch("/dataset/mockIrisSet.json")
      .then((response) => {
        return response.json();
      })
      .then((json) => {
        this.dataSet = json;
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
