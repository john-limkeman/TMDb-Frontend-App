<template>
  <div id="app">
    <img id="logo" src="https://www.themoviedb.org/assets/2/v4/logos/v2/blue_square_2-d537fb228cf3ded904ef09b136fe3fec72548ebc1fea3fbbd1ad9e36364db38b.svg" alt="The Movie Database">
   <br/>
    <select name="typeToggle"  v-model="query.type">
    <option value="all">All</option>
    <option value="movie">Movies</option>
    <option value="tv">TV Shows</option>
    <option value="person">People</option>
    </select>
    <input type="text" v-model="query.text" >
    <button v-on:click="conductSearch()">SEARCH</button>
    <ResultView v-bind:config="api.configuration" v-bind:results="results" v-if="results.length > 0"/>
  </div>
</template>

<script>
import axios from 'axios'
import ResultView from './components/ResultView.vue'
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
          base: "https://api.themoviedb.org/3",
          key: '917369bb118862e487faedc2fa6bf48d',
          params: "&language=en-US&include_adult=false&query=",
          page: "&page=",
          configuration: {},
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
      try{
        axios.get(`${this.api.base}/search/movie?api_key=${this.api.key}${this.api.params}${this.query.text}${this.api.page}${this.query.page}`)
        .then(result =>{
          this.results = result.data.results;
        })
        console.log(this.results)
      } catch(error){
        console.log("error")
      }
    },
    searchTV(){
      console.log("tv search...")
       try{
        axios.get(`${this.api.base}/search/tv?api_key=${this.api.key}${this.api.params}${this.query.text}${this.api.page}${this.query.page}`)
        .then(result =>{
          this.results = result.data.results;
        })
        console.log(this.results)
      } catch(error){
        console.log("error")
      }
    },
    searchPeople(){
      console.log("people search...")
       try{
        axios.get(`${this.api.base}/search/person?api_key=${this.api.key}${this.api.params}${this.query.text}${this.api.page}${this.query.page}`)
        .then(result =>{
          this.results = result.data.results;
        })
        console.log(this.results)
      } catch(error){
        console.log("error")
      }
    }

  },
  components: {
    ResultView
  },
  mounted() {
    
      axios.get(`${this.api.base}/configuration?api_key=${this.api.key}`).then(response => {
        this.api.configuration = response.data;
      })
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
  #logo{
height: 200px;
width: auto;
  }
</style>
