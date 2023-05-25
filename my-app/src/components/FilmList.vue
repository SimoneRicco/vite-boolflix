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
    <Card v-for="item in store.filmList" :key="item.id" :cardData="item"></Card>
  </div>
</template>

<style lang="scss" scoped></style>
