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
        },
        api: {
          base: "",
          key: "",
          params: "&language=en-US&include_adult=false&query="
        }
    }
  },
  methods: {
    conductSearch(){
      console.log(this.query)
      if(this.query.type == "movie"){
        this.searchMovies();
      } else if (this.query.type == "tv"){
        this.searchTV();
      } else{
        this.searchPeople();
      }
    },
    searchMovies(){
      console.log("movie search...")

    },
    searchTV(){
      console.log("tv search...")
    },
    searchPeople(){
      console.log("people search...")
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
