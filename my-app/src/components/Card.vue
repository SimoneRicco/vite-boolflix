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
    <div class="inner-card">
      <div class="card-front">
        <img
          :src="
            cardImg != null ? 'https://image.tmdb.org/t/p/w342/' + cardImg : ''
          "
          alt=""
        />
      </div>
      <div class="card-back">
        <ul>
          <li><span class="title">Nome: </span>{{ cardTitle }}</li>
          <li>
            <span class="title">Nome originale: </span>{{ cardOriginalTitle }}
          </li>
          <li>
            <span class="title">Lingua originale: </span
            ><lang-flag :iso="cardOriginalLanguage" />{{ cardOriginalLanguage }}
          </li>
          <li>
            <span class="title">Valutazione: </span
            ><template v-for="index in 5">
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
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  .title {
    font-weight: bold;
    font-size: 1.1rem;
  }
  .star {
    color: rgb(212, 212, 42);
  }
  ul {
    height: 30%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    list-style: none;
  }
}
/* Flip card*/
.card {
  background-color: transparent;
  width: 342px;
  height: 513px;
  perspective: 1000px;
}

.inner-card {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
}

.card:hover .inner-card {
  transform: rotateY(180deg);
}

.card-front,
.card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.card-front {
  background-color: #bbb;
  color: black;
}

.card-back {
  background-color: black;
  color: white;
  transform: rotateY(180deg);
  padding-top: 2rem;
}
</style>
