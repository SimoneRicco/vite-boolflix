<script>
import { store } from "../store";
export default {
  data() {
    return {
      store,
    };
  },
  methods: {
    search() {
      this.$emit("searching");
    },
  },
};
</script>

<template>
  <header>
    <div class="name">BOOLFIX</div>
    <div class="search">
      <input type="text" v-model="store.searchStr" />
      <button @click="search">Search</button>
    </div>
  </header>
</template>

<style lang="scss" scoped>
header {
  display: flex;
  justify-content: space-between;
}
</style>
