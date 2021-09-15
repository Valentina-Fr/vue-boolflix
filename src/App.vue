<template>
  <div id="app">
    <header class="d-flex justify-content-between align-items-center px-2">
      <h1 class="text-danger">Boolflix</h1>
      <Search @research="searchTerm" placeholder="Cerca"/>
    </header>
    <main>
      <Section :list="movies" title="Movies" id="movies"/>
      <Section :list="series" title="Series" id="series"/>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Search from './components/Search.vue';
import Section from './components/Section.vue';
export default {
  name: 'App',
  components: {
    Search,
    Section
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
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';
@import './scss/style.scss';
</style>
