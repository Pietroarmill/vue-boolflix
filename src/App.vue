<template>
  <div id="app">
    <AppHeader @searchClick="datoCercato($event)" />
    <AppMain :movieArray="this.movies" />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from "axios";

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain,
  },
  data() {
    return {
      wordSearch: '',
      movies: [],
      series: [],
    }
  },
  created() { },
  methods: {
    datoCercato(word) {
      this.wordSearch = word.toLowerCase();
      console.log(this.wordSearch);

      axios.get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: "3879e014591b98424ebc389a9ced879e",
          query: this.wordSearch,
        }
      })
      .then((resp) => {
        resp.data.results.forEach(element => {
          this.movies.push(element);
        });
      })

      axios.get("https://api.themoviedb.org/3/search/tv", {
        params: {
          api_key: "3879e014591b98424ebc389a9ced879e",
          query: this.wordSearch,
        }
      })
      .then((resp) => {
        resp.data.results.forEach(element => {
          this.movies.push(element);
        });
      })

      console.log(this.movies);
    },
  },
};
</script>

<style lang="scss">
@import "./style/common.scss";

body {
  font-family: Arial, Helvetica, sans-serif;
  background-color: #242424;
}
</style>
