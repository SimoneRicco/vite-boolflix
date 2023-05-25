<script>
import { store } from "../store";
import "@fortawesome/fontawesome-free/css/all.css";
export default {
  data() {
    return {
      store,
    };
  },
  props: {
    cardData: Object,
  },
  methods: {
    getRatingFive(toConvert) {
      return Math.floor((toConvert * 5) / 10);
    },
  },
};
</script>

<template>
  <div class="card" v-if="cardData.backdrop_path != null">
    <img
      :src="
        cardData.backdrop_path != null
          ? 'https://image.tmdb.org/t/p/w342/' + cardData.backdrop_path
          : ''
      "
      alt=""
    />
    <div class="title">Nome: {{ cardData.name }}</div>
    <div class="original-title">
      Nome originale:{{ cardData.original_name }}
    </div>
    <div class="original-language">
      Lingua originale:{{ cardData.original_language }}
    </div>
    <div class="vote_average">
      Valutazione: <font-awesome-icon icon="fa-solid fa-star" />
      {{ getRatingFive(cardData.vote_average) }}/5
    </div>
    <img
      :src="
        cardData.origin_country[0] != undefined
          ? 'https://flagsapi.com/' +
            cardData.origin_country[0] +
            '/flat/64.png'
          : ''
      "
      alt="Immagine"
    />
  </div>
</template>

<style lang="scss" scoped>
.card {
  border: 1px solid black;
}
</style>
