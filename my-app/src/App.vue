<script>
import Header from "./components/Header.vue";
import axios from "axios";
import FilmList from "./components/FilmList.vue";
import { store } from "./store";
//https://api.themoviedb.org/3/movie/550?api_key=5272734d98b33c8b70a6cd3f32c035cd
//https://api.themoviedb.org/3/search/movie?query=Avengers&include_adult=false&language=en-US&page=1
export default {
  data() {
    return {
      //api_key: "5272734d98b33c8b70a6cd3f32c035cd",
      store,
    };
  },
  components: {
    Header,
    FilmList,
  },
  methods: {
    getFilms() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "5272734d98b33c8b70a6cd3f32c035cd",
            query: this.store.searchStr,
          },
        })
        .then((response) => (this.store.filmList = response.data.results));
    },
    getSeries() {
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "5272734d98b33c8b70a6cd3f32c035cd",
            query: this.store.searchStr,
          },
        })
        .then((response) => (this.store.seriesList = response.data.results));
    },
  },
  created() {
    this.getFilms();
    this.getSeries();
  },
};
</script>

<template>
  <main>
    <Header @searching="this.getFilms()"></Header>
    <FilmList></FilmList>
  </main>
</template>

<style lang="scss" scoped></style>
