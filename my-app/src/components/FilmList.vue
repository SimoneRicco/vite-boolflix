<script>
import { store } from "../store";
import Card from "./Card.vue";
export default {
  data() {
    return {
      store,
    };
  },
  components: {
    Card,
  },
};
</script>

<template>
  <div class="container">
    <div class="films">Films</div>
    <div class="f-container">
      <Card
        v-for="item in store.filmList"
        :key="item.id"
        :cardImg="item.poster_path"
        :cardTitle="item.title"
        :cardOriginalTitle="item.original_title"
        :cardOriginalLanguage="item.original_language"
        :cardRating="item.vote_average"
      ></Card>
    </div>
    <div class="series">Series</div>
    <div class="s-container">
      <Card
        v-for="item in store.seriesList"
        :key="item.id"
        :cardImg="item.poster_path"
        :cardTitle="item.name"
        :cardOriginalTitle="item.original_name"
        :cardOriginalLanguage="item.original_language"
        :cardRating="item.vote_average"
      ></Card>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.films,
.series {
  font-size: 3rem;
}
.f-container,
.s-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 2rem;
}
</style>
