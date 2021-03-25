<template>
  <div id="app">
    <select name="typeToggle"  v-model="query.type">
    <option value="all">All</option>
    <option value="movie">Movies</option>
    <option value="tv">TV Shows</option>
    <option value="person">People</option>
    </select>
    <input type="text" v-model="query.text">
    <button v-on:click="conductSearch()">SEARCH</button>
    <ResultView v-bind:results="results"/>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
      return{
        results: [],
        chosenItem: [],
        query: {
          text: "",
          page: 1,
          type: "movie",
        }
    }
  },
  methods: {
    conductSearch(){
      console.log(this.query)
    }
  },
  components: {

  }
}
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
