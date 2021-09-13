<template>
  <div id="app">
    <main>
      <Search @research="searchTerm"/>
      <Card :send-list="combineArr"/>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Search from './components/Search.vue';
import Card from './components/Card.vue';
export default {
  name: 'App',
  components: {
    Search,
    Card,
  },
  data(){
    return {
      movies:[],
      series:[],
      baseUri:"https://api.themoviedb.org/3",
      api: "40b3803735afda675d9d9ea1398ce89e",
    }
  },
  methods: {
    searchTerm(query){
      if(!query) this.list = [];
      this.fetchApi(query, "/search/movie", "movies");
      this.fetchApi(query, "/search/tv", "series");
      
    },
    fetchApi(query, endpoint, arr){
      axios.get(`${this.baseUri}${endpoint}?api_key=${this.api}&query=${query}`).then((res)=>
        this[arr] = res.data.results);
    }
  },
  computed: {
    combineArr(){
      return [...this.movies, ...this.series];
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  ul {
    list-style: none;
  } 
}
</style>
