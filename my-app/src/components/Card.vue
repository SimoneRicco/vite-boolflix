<script>
import { store } from "../store";
import "@fortawesome/fontawesome-free/css/all.css";
import LangFlag from "vue-lang-code-flags";
export default {
  data() {
    return {
      store,
    };
  },
  components: {
    LangFlag,
  },
  props: {
    cardImg: String,
    cardTitle: String,
    cardOriginalTitle: String,
    cardOriginalLanguage: String,
    cardRating: Number,
  },
  methods: {
    getRatingFive(toConvert) {
      return Math.floor((toConvert * 5) / 10);
    },
    // getStars(num) {
    //   let toReturn = "";
    //   for (let i = 0; i < 5; i++) {
    //     if (num <= i) {
    //       toReturn += '<font-awesome-icon icon="fa-solid fa-star" />';
    //     } else {
    //       toReturn += '<font-awesome-icon icon="fa-regular fa-star" />';
    //     }
    //   }
    //   return toReturn;
    // },
  },
};
</script>

<template>
  <div class="card" v-if="cardImg != null">
    <!-- Backdrop -->
    <img
      :src="cardImg != null ? 'https://image.tmdb.org/t/p/w342/' + cardImg : ''"
      alt=""
    />
    <div class="title">Nome: {{ cardTitle }}</div>
    <div class="original-title">Nome originale:{{ cardOriginalTitle }}</div>
    <div class="original-language">
      Lingua originale:{{ cardOriginalLanguage }}
    </div>
    <div class="vote_average">
      Valutazione:
      <template v-for="index in 5">
        <template v-if="index <= getRatingFive(cardRating)">
          <font-awesome-icon
            class="star"
            icon="fa-solid fa-star"
            :key="index"
          />
        </template>
        <template v-else>
          <font-awesome-icon
            class="star"
            icon="fa-regular fa-star"
            :key="index"
          />
        </template>
      </template>
    </div>
    <lang-flag :iso="cardOriginalLanguage" />
  </div>
</template>

<style lang="scss" scoped>
.card {
  border: 1px solid black;
  .star {
    color: rgb(212, 212, 42);
  }
}
</style>
