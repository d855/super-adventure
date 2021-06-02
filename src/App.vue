<template>
  <input type="text" v-model="searchTerm">
  <select v-model="serachType">
    <option value="movie" selected>Movies</option>
    <option value="series">Series</option>
    <option value="episode">Episodes</option>
  </select>
  <button @click="searchDb">Search</button>
  <movieList v-bind:movieDetails="this.searchResults" />
</template>

<script>
import movieList from './components/movieList'
import axios from 'axios'

export default {
  name: 'App',
  data(){
    return {
      searchTerm: '',
      serachType: '',
      searchResults: {}
    }
  },
  components: {
    movieList
  },
  methods: {
    searchDb(){
      axios.get('http://www.omdbapi.com/', {
        params: {
          apikey: 'ebdfe023',
          s: this.searchTerm,
          type: this.serachType
        }
      })
          .then((response) => {
            console.log(response.data.Search);
            this.searchResults = response.data.Search;
       })
    }
  }
}
</script>

    MovieList
<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
